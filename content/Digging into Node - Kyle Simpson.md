---
published: true
tags:
  - ✅
sr-due: 2029-05-28
sr-interval: 1930
sr-ease: 290
---

⬅️ [[NodeJS]]

- 🔗 from FEM [Course Digging Into Node Introduction](https://frontendmasters.com/courses/digging-into-node/introduction/)

## Introduction

**🤔 How do I/O compare to CPU tasks in terms of speed?**
I/O are 3-4x slower than CPU tasks which just happen in the processor

- the async event loop is a much better model than threads for the I/O tasks
- node gives you high throughput low latency I/O communication

## Command-line scripts

**🤔 What is POSIX?**
It's a way that C-style programs interact with a linux system.

```javascript
console.log('Hello world')

// is a wrapper for this but with a newline
process.stdout.write('Hello world')

// wrapper for the error stream
console.error()
```

```bash

# go and find node in whatever OS you're one
#! /usr/bin/env node

# making a file executable
chmod u+x file.js
```

- `process.argv`'s first two arguments: path to my node installation, full path to the file
- 💡 You can run `process.argv.slice(2)` to chop them off!

```javascript

// for parsing your argv (-- and - and flags and whatnot)
var args = require("minimist")(process.argv.slice(2))

// to check if a specific argument exists
if (args.help) doSomething()
```

## File System
```js
var contents = fs.readFileSync(filepath)

// if I console.log that I'll just get a buffer
// because console.log was trying to process the value
// to get the string
process.stdout.write(contents)

// or (this is slightly less efficient)
var contents = fs.readFileSync(filepath, 'utf8')
```

## Streams
- simplex stream: you can either read or write to it
- duplex stream: you can do both

```js
var stream1; // readable
var stream2; // writable
stream1.pipe(stream2);

// another readable stream
var stream3 = stream1.pipe(stream2);

let filePath = path.join(BASEPATH,args.file);
processFile(fs.createReadStream(filePath));

function processFile(inputStream) {
	var stream = inputStream;
	var outStream;

	if (args.uncompress) {
		let gunzip = zlib.createGunzip();
		stream = stream.pipe(gunzip);
	}

	# var Transform = require("stream").Transform;
	# this will transform one chunk at a time
	var upperCaseTr = new Transform({
		transform(chunk,encoding,callback) {
			this.push(chunk.toString().toUpperCase());
			callback();
		}
	});

	stream = stream.pipe(upperCaseTr);

	if (args.compress) {
		OUTPATH = `${OUTPATH}.gz`;
		let gzip = zlib.createGzip();
		stream = stream.pipe(gzip);
	}

	if (args.out) {
		outStream = process.stdout;
	}
	else {
		outStream = fs.createWriteStream(OUTPATH);
	}

	stream.pipe(outStream);
}

```

## Gzipping
```js

// a stream representation of gzip
var zlib = require("zlib");

# compressing
if (args.compress) {
	OUTPATH = `${OUTPATH}.gz`;
	let gzip = zlib.createGzip();
	stream = stream.pipe(gzip);
}

# uncompressing
if (args.uncompress) {
	let gunzip = zlib.createGunzip();
	stream = stream.pipe(gunzip);
}
```

Waiting until the end of stream

```js

// helper function
function streamComplete(stream){
	return new Promise(function c(res){
		stream.on("end",res);
	});
}

await streamComplete(outStream)



```

**🤔 What is the advantage of the streaming protocol? (aka why chunks?)**
Not only it's more efficient it also uses less memory (65kb buffer size at a time, by default)

## Database
**🤔 What are advantages of using SqLite?**
Unlike MySQL, lite doesn't require a db server, instead, it's a serverless embedded db that runs as part of the application. It cannot connect to any other application over the network. It's super lightweight and ideal for small sets of data.

How to join a table
```js
async function getAllRecords() {
	var result = await SQL3.all(
		`
		SELECT
			Something.data AS "something",
			Other.data AS "other"
		FROM
			Something
			JOIN Other ON (Something.otherID = Other.id)
		ORDER BY
			Other.id DESC, Something.data
		`
	);

	return result;
}
```

## Web servers
Express routing and static file serving
```js
#!/usr/bin/env node

"use strict";

var util = require("util");
var path = require("path");
var http = require("http");

var express = require("express");
var app = express();
var sqlite3 = require("sqlite3");


// ************************************

const DB_PATH = path.join(__dirname,"my.db");
const WEB_PATH = path.join(__dirname,"web");
const HTTP_PORT = 8039;

var delay = util.promisify(setTimeout);

// define some SQLite3 database helpers
//   (comment out if sqlite3 not working for you)
var myDB = new sqlite3.Database(DB_PATH);
var SQL3 = {
	run(...args) {
		return new Promise(function c(resolve,reject){
			myDB.run(...args,function onResult(err){
				if (err) reject(err);
				else resolve(this);
			});
		});
	},
	get: util.promisify(myDB.get.bind(myDB)),
	all: util.promisify(myDB.all.bind(myDB)),
	exec: util.promisify(myDB.exec.bind(myDB)),
};

var httpserv = http.createServer(app);

main();


// ************************************

function main() {
	defineRoutes(app);

	httpserv.listen(HTTP_PORT);
	console.log(`Listening on http://localhost:${HTTP_PORT}...`);
}

function defineRoutes(app) {
	app.get(/\/get-records\b/,async function getRecords(req,res){
		await delay(1000);

		let records = await getAllRecords() || [];

		// res.json(records);

		res.setHeader("Content-Type","application/json");
		res.setHeader("Cache-Control","max-age: 0, no-cache");
		res.writeHead(200);
		res.end(JSON.stringify(records));
	});

	app.use(function rewriter(req,res,next){
		if (/^\/(?:index\/?)?(?:[?#].*$)?$/.test(req.url)) {
			req.url = "/index.html";
		}
		else if (/^\/js\/.+$/.test(req.url)) {
			next();
			return;
		}
		else if (/^\/(?:[\w\d]+)(?:[\/?#].*$)?$/.test(req.url)) {
			let [,basename] = req.url.match(/^\/([\w\d]+)(?:[\/?#].*$)?$/);
			req.url = `${basename}.html`;
		}

		next();
	});

	var fileServer = express.static(WEB_PATH,{
		maxAge: 100,
		setHeaders(res){
			res.setHeader("Server","Node Workshop: ex6");
		}
	});

	app.use(fileServer);

	app.get(/\.html$/,function friendly404(req,res,next){
		req.url = "/404.html";
		fileServer(req,res,next);
	});
}

// *************************
// NOTE: if sqlite3 is not working for you,
//   comment this version out
// *************************
async function getAllRecords() {
	var result = await SQL3.all(
		`
		SELECT
			Something.data AS "something",
			Other.data AS "other"
		FROM
			Something
			JOIN Other ON (Something.otherID = Other.id)
		ORDER BY
			Other.id DESC, Something.data
		`
	);

	return result;
}

```

## Child process
- how to deal with node across multiple processes, specifically how to spin up child processes from our main process
- one way of testing whether a command was successfully run (aka non 0 exit code), is to chain another command after it. If the original command errored it will immediately exit and not run the next command, e.g.: `node index.js && ls -la`

## Debugging
- go to chrome inspect and when you run add the `--inspect` flag