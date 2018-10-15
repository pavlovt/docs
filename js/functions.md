# Functions

- what is it
- console.log
- return values, default return value, code after return
- var and functions in functions
- closure
- recursion
```js
function power(base, exponent) {
  if (exponent == 0) {
    return 1;
  } else {
    return base * power(base, exponent - 1);
  }
}

console.log(power(2, 3));
// → 8
```
it is quicker to use loops - speed and maintainability
- functional programming and side effects
