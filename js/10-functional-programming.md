# Functional Programming

## A Function in Mathematics
```
f (X) = Y
```
The statement can be read as “A function f, which takes X as its argument, and returns the output Y.” X and Y can be any number, for instance. That’s a very simple definition. There are key takeaways in the definition, though:
- A function must always take an argument.
- A function must always return a value.
- A function should act only on its receiving arguments
(i.e., X), not the outside world.
- For a given X, there will be only one Y.

### Non functional way
```js
var percentValue = 5;
var calculateTax = (value) => { 
    return value/100 * (100 + percentValue) 
}
```
Here percentValue is hidden argument which makes the function unpredictable (everyone can change percentValue which changes the function output)

### Functional way
```js
var percentValue = 5;
var calculateTax = (value) => { 
    return value/100 * (100 + percentValue) 
}
```
Here we don't have hidden arguments. This makes it easy for testing.

## Imperative, Declarative, Abstraction
Functional programming is also about being declarative and writing abstracted code.
```js
var array = [1,2,3]
for(i=0;i<array.length;i++)
console.log(array[i]) //prints 1, 2, 3
```
this is the imperative approach - it explains **how** to do it

```js
var array = [1,2,3]
array.forEach((element) => console.log(element))
//prints 1, 2, 3
```
the declarative approach explains **what** to do but does not care how is it done (forEach function is a black box, abstract function for us)

Functional programming is about creating functions in an abstracted way that can be reused by other parts of the code. 

## Learn more
- Beginning Functional JavaScript, second edition