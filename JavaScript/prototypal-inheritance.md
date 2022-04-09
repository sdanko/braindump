# Prototypal inheritance

As prototypes are powerful and flexible feature, they also allow us to implement inheritance. Inheritance can be implemented using the concept of subtyping. The idea of subtyping is to create a new constructor that is based on an existing one. The new constructor is called the sub-constructor, the existing one the super-constructor. In the following example, `Student` is a subtype of `Person`:

```
function Student(name, score) {
  Person.call(this, name);
  this.score = score;
}
Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;
Student.prototype.hello = function() {
  return `${Person.prototype.hello.call(this)} My score is ${this.score}!`;
};

const s = new Student('Frodo', 5);
console.log(s.hello());
``` 
In the previous example `Student` is sub-constructor of `Person`. `Student` constructor sets up instance property `name` by calling `Person`. `Person` constructor is called as a function, but the `call()` method allows us to keep `this` of `Student`.

By  making `Student.prototype` prototype of `Person,prototype`, we can use methods from `Person`. This is done with `Object.create`. After this, we need to reset the constructor property `Student.prototype`.

Resources:
- https://2ality.com/2012/01/js-inheritance-by-example.html
