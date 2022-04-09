# Prototype chain

Unlike Java, C#, C++, and Python (among many others), JavaScript is not a class-based language. While there is a `class` keyword in JavaScript since 2015, it’s only syntactic sugar. Under the hood, JavaScript uses the mechanism known as the prototype chain.

Every object in JavaScript has a built-in property which represents the objects **prototype**. The prototype is itself an object. Every prototype can have its own prototype, making what's called a **prototype chain**. This chain ends when we reach the objects that has `null` for its prototype.

###Prototype properties

We can encounter different types of object properties that are related to prototype. They are important for understanding the concept of **prototype chain**.

- **[[Prototype]]** is a hidden internal property that all objects have in JavaScript, it holds a reference to the object’s prototype. That property is called internal, because it only exists in the language specification and cannot be directly accessed from JavaScript.

- **\_\_proto\_\_**  is a property of `Object.prototype` that exposes the hidden `[[Prototype]]` property of an object and allows you to access or modify it. This property should not be used since its deprecated. The standard way to access an object's prototype is the `Object.getPrototypeOf(`) method. You can also modify an object’s prototype using `Object.setPrototypeOf()` method.

- **Function.property** is a property that all functions have except arrow functions. It is only used when a function is invoked as a constructor function. It is the blueprint for creating objects by using that (constructor) function with new keyword.

## Object literals

Although it is not encouraged, it is possible to use `\_\_proto\_\_`  to specify the prototype of the object that is created.

```
const parent = { proto: true };

const obj = {
	__proto__: parent,
  foo: { value: 123 },
  bar: { value: "abc" }
};

console.log(obj.proto); // true
``` 
In an object literal, property key `\_\_proto\_\_` is a special operator for specifying the prototype of the created objects.

## Object.create

The `Object.create()` method creates a new object and allows you to specify an object that will be used as the new object's prototype. This is the example:

```
const parent = { proto: true };

const obj = Object.create(parent, {
  foo: { value: 123 },
  bar: { value: "abc" }
});

console.log(obj.proto); // true
``` 

## Constructors

As already mentioned, all functions have a property named `prototype`. When calling function as a constructor, this property is set as the prototype of the newly constructed object.

```
function Person(name) {
  this.name = name;
}

Person.prototype = {
  hello() {
    return `My name is ${this.name}!`;
  }
};

Person.prototype.constructor = Person;

const p = new Person('Frodo');
console.log(p.hello());
``` 

When `Person` function is executed with `new Person()`, it sets up the fresh object passed to it via the implicit parameter `this`. This fresh object is (implicitly) returned by the constructor and considered its instance. So, in this case, `p` is an instance of `Person`.

To avoid storing methods in every instance, they are defined in the `prototype` object. This way, we save up memory and introduce a separation of responsibility: The constructor is responsible for setting up instance-specific data, the prototype contains shared data (i.e., the methods).

After setting up the prototype of the `Person` constructor, there is a problem. For every function f the following equation should hold: `f.prototype.constructor === f`. But since we have replaced the default value of `Person.prototype`, this is no longer the case. That's why we use the following line: `Person.prototype.constructor = Person`. It sets the prototype's constructor property to the function used to create Person objects. Another option would be to keep the default value of the prototype object and add methods directly to it:

```
Person.prototype.hello = function () {
  console.log(`My name is ${this.name}!`);
};
``` 

Resources:
- https://medium.com/@eamonocallaghan/prototype-vs-proto-vs-prototype-in-javascript-6758cadcbae8
- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Object_prototypes#setting_a_prototype
- https://2ality.com/2015/09/proto-es6.html
