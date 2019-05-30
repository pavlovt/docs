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
- arguments
  
## Closures
```js
var createPet = function(name) {
  // private property
  var sex;

  // private function
  function do Something() {}
  
  return {
    // public function
    setName: function(newName) {
      name = newName;
    },
    
    getName: function() {
      return name;
    },
    
    getSex: function() {
      return sex;
    },
    
    setSex: function(newSex) {
      if(typeof newSex === 'string' && (newSex.toLowerCase() === 'male' || 
        newSex.toLowerCase() === 'female')) {
        sex = newSex;
      }
    }
  }
}

var pet = createPet('Vivie');
pet.getName();                  // Vivie

pet.setName('Oliver');
pet.setSex('male');
pet.getSex();                   // male
pet.getName();                  // Oliver
```

## Execution context
Execution context (EC) is defined as the environment in which JavaScript code is executed. By environment I mean the value of this, variables, objects, and functions JavaScript code has access to, constitutes it’s environment.

- global ec
- functionsl ec
- eval ec

```js
var a = 10;

function functionA() {

	console.log("Start function A");

	function functionB(){
		console.log("In function B");
	}

	functionB();

}

functionA();

console.log("GlobalContext");
```
## What is “this” Context
```js
var obj = {
    foo: function() {
        return this;   
    }
};

obj.foo() === obj; // true
```

```js
function foo() {
    alert(this);
}

foo() // window
new foo() // foo
```
### Eval
```js
var x = 17;                                       //a local variable
var evalX = eval("'use strict'; var x = 42; x");  //eval an x internally
assert(x === 17);                                 //x is still 17 here
assert(evalX === 42);                             //evalX takes 42 from eval'ed x

function foo() {
    "use strict";

     var x = 17;
     var evalX = eval("var x = 42; x");
     assert(x === 17);
     assert(evalX === 42);
}
```

Stricct mode makes those changes:
- Eliminates some JavaScript silent errors by changing them to throw errors.
- Fixes mistakes that make it difficult for JavaScript engines to perform optimizations: strict mode code can sometimes be made to run faster than identical code that's not strict mode.
- Prohibits some syntax likely to be defined in future versions of ECMAScript.

Important notes:
- do not use eval if possible and never execute inside data provided by the user (this data is considered insecure)
- do not use strict mode on a global scope: some libs may stop working

## Changing the 'this' context

```js
function user(firstName, lastName, age) {
    // do something 
}

user.call(window, 'John', 'Doe', 30);
user.apply(window, ['John', 'Doe', 30]);

function Widget() {
    this.element = document.createElement('div');
    this.element.addEventListener('click', this.onClick.bind(this), false);
}

Widget.prototype.onClick = function(e) {
    // do something
};
```

## Higher-Order Functions
A higher-order function is a function that can take another function as an argument, or that returns a function as a result.

## Learn more
- [Exercises](https://github.com/pavlovt/docs/blob/master/js/3-functions.exercise.md)
- [Functions](http://eloquentjavascript.net/03_functions.html)
- [Defining functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Functions)
- [Execution context, Scope chain and JavaScript internals](https://hackernoon.com/execution-context-in-javascript-319dd72e8e2c)
- [Strict Mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode)
