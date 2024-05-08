---
published: true
tags:
  - ✅
sr-due: 2026-01-13
sr-interval: 791
sr-ease: 250
---
⬅️ [[Execute Program Advanced TypeScript]]

## Mapped types
- We can think of `Partial` as "mapping" the object type's properties into a new set of properties
```ts
type User = {
  email: string
};

type UserAggregate = {
	// mapping over the user properties
  [K in keyof User]: Array<string>
};

const userAggregate: UserAggregate = {
  email: ['amir@example.com'],
};
userAggregate.email;


// with two properties, respecting the type
type User = {
  email: string
  age: number
};

type UserAggregate = {
  [K in keyof User]: Array<User[K]>
};

const userAggregate: UserAggregate = {
  email: ['amir@example.com'],
  age: [36],
};
userAggregate;
```