# Values, Types and Operators

## Values
bits, bytes...

## Numbers
- 64 bits
- limit: 10^n
- integers and floats
- operator precedence (100 + 4)* 11

## Strings
- "str 1" or 'str 2' or `multiline string``
- only 1 type of strings should be used in the whole project
- the string is an object - try it and see it's methods
- concatination: 'str 1' + 'str 2'
- template literal: `half of 100 is ${100 / 2}``
- the string is an array
  
```JavaScript
console.log(typeof 4)
// → number
console.log(typeof "4")
// → string
```
## Boolean
```JavaScript
console.log(3 > 2)
// → true
console.log(3 < 2)
// → false
console.log("Aardvark" < "Zoroaster")
// → true
console.log("Itchy" != "Scratchy")
// → true
console.log("Apple" == "Orange")
// → false
console.log(NaN == NaN)
// → false
```

## Logical operations
```JavaScript
console.log(true && false)
// → false
console.log(true && true)
// → true

console.log(false || true)
// → true
console.log(false || false)
// → false
```
### the precedence of the logical operators:
```JavaScript
console.log((true || false) && true)
// → true
console.log(true || false && true)
// → true
```
### not operator:
```JavaScript
console.log(!true)
// → false
console.log(!false)
// → true

console.log(!!true)
// → true
console.log(!!false)
// → false
```
### == or ===

### ternary operator: 
```JavaScript
console.log(true ? 1 : 2);
// → 1
console.log(false ? 1 : 2);
// → 2
```
### unorthodox usage
obj && obj.prop1 || {}

## Empty values
undefined or null

## Type conversion
```JavaScript
console.log(typeof "4")
// string
console.log(typeof +"4")
// number
console.log(typeof +"f4")
// NaN
console.log(8 * null)
// → 0
console.log("5" - 1)
// → 4
console.log("5" + 1)
// → 51
console.log("five" * 2)
// → NaN
console.log(false == 0)
// → true
```

## Objects
```JavaScript
{
    prop1: 'val1'
    fun1: () => { ... }
}
```

### access a property
```JavaScript
z = {x:1, y:2}
// {x: 1, y: 2}
z.x
// 1
z['x']
// 1
```

### delete a property
```JavaScript
z = {x:1, y:2}
// {x: 1, y: 2}
delete z.x
// true
z
// {y: 2}
```

## Arrays
```JavaScript
[1, 2, 3]
```

### access a property
```JavaScript
z = [1, 2, 3]
// [1, 2, 3]
z[0]
// 1
```

### delete a property
```JavaScript
z = [1, 2, 3]
// [1, 2, 3]
delete z.x
// true
z
// [empty, 2, 3]
```

```JavaScript
z = [1, 2, 3]
// [1, 2, 3]
z.splice(0, 1)
// [1]
z
// [2, 3]
```

be careful not to create an array and use it as an object or the oposite - the result is very strange