---
tags:
  - ✅
sr-due: 2025-01-09
sr-interval: 100
sr-ease: 316
---
⬅️ [[JavaScript]]
🔗 [Stack Overflow](https://stackoverflow.com/questions/37576685/using-async-await-with-a-foreach-loop)
## Reading in sequence

If you want to read the files in sequence, **you cannot use `forEach`**. Just use a modern `for … of` loop instead, in which `await` will work as expected:

```javascript
async function printFiles () {
  const files = await getFilePaths();

  for (const file of files) {
    const contents = await fs.readFile(file, 'utf8');
    console.log(contents);
  }
}
```

## Reading in parallel

If you want to read the files in parallel, **you cannot use `forEach`**. Each of the `async` callback function calls does return a promise, but you're throwing them away instead of awaiting them. Just use `map` instead, and you can await the array of promises that you'll get with `Promise.all`:

```javascript
async function printFiles () {
  const files = await getFilePaths();

  await Promise.all(files.map(async (file) => {
    const contents = await fs.readFile(file, 'utf8')
    console.log(contents)
  }));
}
```


## Another example
Problem
```js
const userIds = [1, 2, 3];

async function fetchUsers() {
  userIds.forEach(async (id) => {
    try {
      const user = await fetchUserById(id);
      console.log(`Fetched user: ${user.name}`);
    } catch (error) {
      console.error(`Failed to fetch user with ID ${id}:`, error);
    }
  });
}

async function fetchUserById(id) {
  return new Promise((resolve) => {
    let delay = Math.random() * 1000 + 1000;
    setTimeout(() => {
      resolve({ id, name: `User${id}` });
    }, delay);
  });
}

fetchUsers();
```

Solution
The `forEach` loop is synchronous, meaning it doesn’t wait for the inner async function to complete. This results in the data potentially being out of order when logged to the console. To fix this, you can use a `for...of`loop with `await`:

```js
const userIds = [1, 2, 3];

async function fetchUsers() {
  for (const id of userIds) {
    try {
      const user = await fetchUserById(id);
      console.log(`Fetched user: ${user.name}`);
    } catch (error) {
      console.error(`Failed to fetch user with ID ${id}:`, error);
    }
  }
}

async function fetchUserById(id) {
  return new Promise((resolve) => {
    let delay = Math.random() * 1000 + 1000;
    setTimeout(() => {
      resolve({ id, name: `User${id}` });
    }, delay);
  });
}

fetchUsers();
```