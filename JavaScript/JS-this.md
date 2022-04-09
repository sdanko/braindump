# `this` in JavaScript

Invocation of the function is the act of calling the function. Context of an invocation is the value of `this` within function body. This value depends on the invocation pattern. In JavaScript there are 4 invocation patterns:
- function invocation: `alert('Hello World!')`
- method invocation: `console.log('Hello World!')`
- constructor invocation: `new RegExp('\\d')`
- indirect invocation: `alert.call(undefined, 'Hello World!')`

## Function invocation

When a function is not the property of an object, then it is invoked as a function. When a function is invoked this way, `this` is bound to the global object. In a browser, the global object is `window` object.

```
function sum(a, b) {
  console.log(this === window); // => true
  this.myNumber = 20; // add 'myNumber' property to global object
  return a + b;
}
// sum() is invoked as a function
// this in sum() is a global object (window)
sum(15, 16);     // => 31
window.myNumber; // => 20
``` 

On the other hand, while in `strict` mode, `this` is undefined in function invocation.

```
function multiply(a, b) {
  'use strict'; // enable the strict mode
  console.log(this === undefined); // => true
  return a * b;
}
// multiply() function invocation with strict mode enabled
// this in multiply() is undefined
multiply(2, 5); // => 10
``` 

## Method invocation

When a function is stored as a property of an object, we call it a method. When a method is invoked, this is bound to that object.

```
const calc = {
  num: 0,
  increment() {
    console.log(this === calc); // => true
    this.num += 1;
    return this.num;
  }
};

// method invocation. this is calc
calc.increment(); // => 1
calc.increment(); // => 2
``` 

**Extracted methods**

A method can be extracted from an object into a variable. When method is called using this variable, then a function invocation happens, where `this` is the global object `window` or `undefined` in strict mode.

```
var name = 'London';
var obj = {
    name: 'Berlin',
    getName: function(){ 
        var name = 'Rome';
        return this.name; 
        
    }
}

var sample = obj.getName;
console.log(sample()) // London, name variable from global scope
``` 

## Constructor invocation

If a function is invoked with the `new` prefix, then a new object will be created with a  link to the value of the function's prototype member, and `this` will be bound to that new object.

```
function Foo () {
  // this is fooInstance
  this.property = 'Default Value';
}

Foo.prototype.changeProp = function () {
	this.property = 'New value';
};

// Constructor invocation
const fooInstance = new Foo();
console.log(fooInstance.property); // => 'Default Value'
fooInstance.changeProp();
console.log(fooInstance.property); // => 'New Value'
``` 

## Indirect invocation

Because JavaScript is a functional object-oriented language, functions can have methods. Among others, `Function` type objects have `call` and `apply` methods.

Indirect invocation is performed when a function is called using `call()` or `apply()` methods. These methods allow us to pass the context of the invocation as the first argument. Also, they  allow us to  construct an array of arguments to use to invoke a function.

```
function sum(number1, number2) {
  return number1 + number2;
}

sum.call(undefined, 10, 2);    // => 12
sum.apply(undefined, [10, 2]); // => 12
``` 

## Bound function

`Function` object types also have a `bind` method. This method binds function context and/or arguments to specific values. Contrary to `apply()` and `call()` methods, which invoke the function right away, the `bind()` method only returns a new function supposed to be invoked later.

```
const city = {
  name: 'Paris',
  getName() {
    return this.name;
  }
};

// Create a bound function
const boundGetName = city.getName.bind(city);
console.log(boundGetName()); // => Paris

// Extract method from object
const getName = city.getName;
console.log(getName()); // => undefined or throws an error in strict mode
``` 

## Arrow functions

The arrow function doesn't create its own execution context but takes this from the outer function where it is defined. This means that the arrow function resolves `this`lexically. An arrow function is bound with lexical `this` and it cannot be changed even with using `call`, `apply` or `bind` methods.

```
var name = 'Berlin';
const city = {
  name: 'Paris',
  getName: () => {
    return this.name;
  }
};

console.log(city.getName()); // => Berlin, bound lexically to global scope
``` 


## ES6 modules

One thing to keep in mind is that `this` is `undefined` inside the context of an ES6 modules.

```
<script type="module">
    // `this` is undefined
    console.log(this === undefined); // true
</script>
``` 

Resources:
- https://www.codementor.io/@dariogarciamoya/understanding-this-in-javascript-with-arrow-functions-gcpjwfyuc
- https://dmitripavlutin.com/gentle-explanation-of-this-in-javascript/
