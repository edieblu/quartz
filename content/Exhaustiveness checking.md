---
published: true
tags:
  - ✅
sr-due: 2025-09-01
sr-interval: 183
sr-ease: 250
---
⬅️ [[FEM TypeScript Fundamentals]]

 ## Exhaustiveness checking
- Exhaustive" means "considering all possibilities"
```ts
function getName(hasName: User | Cat | Dog, names: string[]): true {
  switch (hasName.kind) {
    case 'user':
      names.push(hasName.userName);
      return true;
	// OR
	  //case 'user':
      //return hasName.userName;
    case 'cat':
      names.push(hasName.catName);
      return true;
    case 'dog':
      names.push(hasName.dogName);
      return true;
  }
}

const names: string[] = [];
getName({kind: 'user', userName: 'Amir'}, names);
getName({kind: 'cat', catName: 'Ms. Fluff'}, names);
getName({kind: 'dog', dogName: 'Woofy'}, names);

names;

//Result:

['Amir', 'Ms. Fluff', 'Woofy']
```
- The `true` value isn't useful to us at runtime, but we have to return something in order to use exhaustiveness checking.
- Generally, we associate exhaustiveness checking with `switch`. However, it works with `if` as well.
- In TypeScript, providing a `default:` inside of our `switch` effectively disables exhaustiveness checking.

So in summary when using `switch`:
1.  Put the `switch` inside of a function where each case `return`s.
2.  Give the function an explicit return type.
3.  Don't add a `default` unless you're very sure that you need one.