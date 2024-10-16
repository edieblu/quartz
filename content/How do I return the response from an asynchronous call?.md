---
tags:
  - ✅
sr-due: 2024-11-03
sr-interval: 36
sr-ease: 276
---

⬅️ [[JavaScript]]
🔗 [Stack Overflow](https://stackoverflow.com/questions/14220321/how-do-i-return-the-response-from-an-asynchronous-call)

The ECMAScript version released in 2017 introduced _syntax-level support_ for asynchronous functions. With the help of `async` and `await`, you can write asynchronous in a "synchronous style". The code is still asynchronous, but it's easier to read/understand.

`async/await` builds on top of promises: an `async` function always returns a promise. `await` "unwraps" a promise and either result in the value the promise was resolved with or throws an error if the promise was rejected.

```js
  async function saveUsers(){
     try{
        let users = await getUsers()
        saveSomewhere(users);
     }
     catch(err){
        console.error(err);
     }
  }

```