# Hoisting

Hoisting is the mechanism of moving the variables and functions declaration to the top of the function scope (or global scope if outside any function). All declarations are hoisted to the top of their scope. However, `let` and `const` use a concept called `Temporal dead zone(TDZ)`, which means there is a period between entering scope and being declared where they return `ReferenceError` when trying to access them. In contrast, if we try to access `var` before deceleration, it will return `undefined`. Also, `var` declarations has a function scope, whereas `let` and `const` have block scope.

This example embodies all the the mentioned concepts:

```
function isTruthy(value) {
  //var has function scope, so it is accessible but returns undefined
  console.log(myVariable2);
  var myVariable = 'Value 1';
  if (value) {
    var myVariable2 = 'Value 2';
    /**
     * temporal dead zone for myVariable
     */
    // Throws ReferenceError: myVariable is not defined
    console.log(myVariable);
    let myVariable = 'Value 3';
    // end of temporary dead zone for myVariable
    console.log(myVariable); // => 'Value 3'
    return true;
  }
  return false;
}
isTruthy(1); // => true
``` 


Resources:
- https://2ality.com/2019/05/unpacking-hoisting.html
- https://dmitripavlutin.com/javascript-hoisting-in-details
