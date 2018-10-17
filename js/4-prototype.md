# Prototype inheritance

##  The prototype is a reference to another object and it is used whenever JS can’t find the property you’re looking for on the current object.

Each time your script attempts to read or write a property of an object,
JavaScript follows a specific sequence in search of a match for the property name.
The sequence is as follows:
1. If the property has a value assigned to the current (local) object, this is the
value to use.
2. If there is no local value, check the value of the property’s prototype of the
object’s constructor.
3. Continue up the prototype chain until either a match of the property is found
(with a value assigned to it) or the search reaches the native Object object.

- using a function as a constructor
```js
function Animal(name) {
    this.name = name;
}

Animal.prototype.sleep = function() {
    console.log(this.name + ': Zzz...');
}

function Dog(name) {
    this.name = name;
}

// Create a reference for the prototype
// why using new keyword?
Dog.prototype = Object.create(new Animal());

Dog.prototype.makeSound = function() {
    console.log(this.name + ': Woof woof!');
}

var dog = new Dog('Lassie');
dog.makeSound(); // Lassie: Woof woof!
dog.sleep(); // Lassie: Zzz...
dog.missing(); // Throws Error
```
- using an object as prototype
```js
var o = {
  a: 2,
  m: function() {
    return this.a + 1;
  }
};

console.log(o.m()); // 3
// When calling o.m in this case, 'this' refers to o

var p = Object.create(o);
// p is an object that inherits from o

p.a = 4; // creates a property 'a' on p
console.log(p.m()); // 5
// when p.m is called, 'this' refers to p.
// So when p inherits the function m of o, 
// 'this.a' means p.a, the property 'a' of p
// The full prototype chain looks loke:
// {a: 4} ---> {a: 2, m: function} ---> Object.prototype ---> null
```

## Where the prototype lives
If we write this:
```js
function doSomething(){}
doSomething.prototype.foo = "bar"; // add a property onto the prototype
var doSomeInstancing = new doSomething();
doSomeInstancing.prop = "some value"; // add a property onto the object
console.log( doSomeInstancing );
```
the result will be:
```js
{
    prop: "some value",
    __proto__: {
        foo: "bar",
        constructor: ƒ doSomething(),
        __proto__: {
            constructor: ƒ Object(),
            hasOwnProperty: ƒ hasOwnProperty(),
            isPrototypeOf: ƒ isPrototypeOf(),
            propertyIsEnumerable: ƒ propertyIsEnumerable(),
            toLocaleString: ƒ toLocaleString(),
            toString: ƒ toString(),
            valueOf: ƒ valueOf()
        }
    }
}
```

## Learn more
- [Inheritance and the prototype chain
](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
- [Understanding JavaScript: Prototype and Inheritance](https://hackernoon.com/understanding-javascript-prototype-and-inheritance-d55a9a23bde2)
- JavaScript Bible
- [exercise](https://www.w3resource.com/javascript-exercises/javascript-object-exercises.php)