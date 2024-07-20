---
tags:
  - ✅
published: true
sr-due: 2027-03-25
sr-interval: 1001
sr-ease: 250
---
⬅️ [[FEM TypeScript Fundamentals]]
#✅ 

## Enum
- "Enum" is short for "enumeration", which means "mentioning things one by one"
- Enums values aren't limited to strings. In fact, if we leave off the enum's values, TypeScript will automatically give them number values, starting with 0
```ts
enum HttpMethod {
  Get = 'GET',
  Post = 'POST',
}
const method: HttpMethod = HttpMethod.Post;
method;

// Result:
'POST'
```
- When referencing enum values, we're forced to use their symbolic names, like `HttpMethod.Post` above. Unlike union types, we're not allowed to directly use the literal value.
```ts
enum HttpMethod {
  Get = 'GET',
  Post = 'POST',
}
const method: HttpMethod = 'POST';
method;

// Result:
type error: Type '"POST"' is not assignable to type 'HttpMethod'.

// the value automatically increases
enum DatabaseType { Postgres = 50, MySql }
const databaseType: DatabaseType = DatabaseType.MySql;
databaseType;

//Result:
51
```
- When an enum member's value changes, we don't have to change any other code. With a union, we might have to update the value in many places. This is a benefit of enums, but a very minor one. Types like these don't change very often, and it's easy to update union values by following the type errors. The code maintenance argument for enums isn't very strong.
- We recommend avoiding enums for two reasons. First, enums break TypeScript's core "type-level extension" rule, complicating our mental model of the language. Second, unions can do the same thing as enums, allowing only a certain set of literal types, with no major drawbacks. However, it's still good to have a basic familiarity with enums because they're sometimes used in real-world code, especially in older TypeScript codebases.