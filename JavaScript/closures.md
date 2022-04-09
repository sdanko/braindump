# Closures

Before understanding closures, it is important to understand the concept of scopes and lexical scopes:

- Scope of a variable or a function is the region of a program where it can be accessed. JavaScript’s scopes are static (they don’t change at runtime) and they can be nested. This means that inside the inner scope you can access variables of outer scopes.

- Lexical scope is the definition area of a variable or a function.

A closure is the combination of a function bundled together (enclosed) with the lexical environment. Simpler, the closure is a function that remembers the variables from the place where it is defined, regardless of where it is executed later. Here is the example:

```
function outerFunc() {
  let outerVar = 'I am outside!';
  function innerFunc() {
    console.log(outerVar); // => logs "I am outside!"
  }
  return innerFunc;
}

function exec() {
  const myInnerFunc = outerFunc();
  myInnerFunc();
}

exec();
``` 
`innerFunc()` still has access to `outerVar` from its lexical scope, even being executed outside of its lexical scope.

## Currying

Currying, an important concept of functional programming, is also possible thanks to closures:

```
function multiply(a) {
  return function executeMultiply(b) {
    return a * b;
  }
}

const double = multiply(2);
double(3); // => 6
double(5); // => 10
const triple = multiply(3);
triple(4); // => 12
``` 
`executeMultiply(b)` is a closure that captures a from its lexical scope. When the closure is invoked, the captured variable a and the parameter b are used to calculate a * b.

## Memoization

Another concept, called memoization is also implemented using closures. Memoization is optimization technique that stores the results of expensive function calls and returns the cached results when same inputs are supplied again. This is the example of the enclosing function that is used to cache return values of inner function:

```
function memoizer(fun) {
  let cache = {};

  return function(n) {
    if (cache[n] != undefined ) {
      return cache[n];
    } else {
      const result = fun(n);
      cache[n] = result;

      return result;
    }
}

const memoFunction = memoizer(expensiveFunction);
memoFunction(n);
``` 


Resources:
- https://dmitripavlutin.com/simple-explanation-of-javascript-closures/#4-the-closure
- https://2ality.com/2019/07/global-scope.html
- https://www.freecodecamp.org/news/javascript-lexical-scope-tutorial/
- https://dheerajmnk.hashnode.dev/scope-in-javascript-understanding-lexical-environment-and-scope-chain
- https://www.better.dev/understanding-memoization-in-javascript
