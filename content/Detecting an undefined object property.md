---
tags:
  - ✅
sr-due: 2024-10-28
sr-interval: 12
sr-ease: 276
---

⬅️ [[JavaScript]]
🔗 [Stack Overflow](https://stackoverflow.com/questions/27509/detecting-an-undefined-object-property)

The usual way to check if the value of a property is the special value `undefined`, is:
```javascript
if(o.myProperty === undefined) {
  alert("myProperty value is the special value `undefined`");
}
```
To check if an object does not actually have such a property, and will therefore return `undefined` by default when you try to access it:
```javascript
if(!o.hasOwnProperty('myProperty')) {
  alert("myProperty does not exist");
}
```
To check if the value associated with an identifier is the special value `undefined`, _or_ if that identifier has not been declared:

```javascript
if(typeof myVariable === 'undefined') {
  alert('myVariable is either the special value `undefined`, or it has not been declared');
}
```