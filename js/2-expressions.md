# Expressions and Statements

- Expression: a fragment of code that produces a value
- Statement: an expression finishing at the end of the line or with semicolumn 


```javascript
1 + 2;

1
+ 
2;

1
+ 
2
;
```

## Variables
var, let, const, global, local scope
```js
let x = 10;
if (true) {
  let y = 20;
  var z = 30;
  console.log(x + y + z);
  // → 60
}
// y is not visible here
console.log(x + z);
// → 40
```

## Conditional exedcution
```js
let theNumber = Number(prompt("Pick a number"));
if (!Number.isNaN(theNumber) && theNumber > 100) {
  console.log("you entered big number");
} else if (!Number.isNaN(theNumber) && theNumber < 100) {
  console.log("you entered small number");
} else {
  console.log("you did not enter a number");
}
```

```js
if (1 + 1 == 2) console.log("It's true");
// → It's true
```
- do not use too much ifs
- alternative (cons)
```js
switch (varName) {
   case "afshin":
   case "saeed":
   case "larry": 
       alert('Hey');
       break;

   default: 
       alert('Default case');
}
```
- alternative: const z = {x: ()=> {...}, y: ()=> {...}}; z(x);

## Loops
- while (x < 10) { x--; ... }
- do { x--; ... } while (x < 10)
- for (let number = 0; number <= 12; number++) { ... break; continue; }

## Comments
```js
// code block description
some code

/**
 * Convert a string containing two comma-separated numbers into a point.
 * @param {string} str - The string containing two comma-separated numbers.
 * @return {Point} A Point object.
 * @example 
 * fromString('1,2,3') returns {x: 1, y: 2, z: 3}
 */
fromString(str) {
 ...
}
```