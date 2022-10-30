# Recursion

Recursion is a function that calls itself.

Whenever we use recursion, we need to remember about the base case.

Base case: 
- Final stop point, the condition where loop needs to stop calling itself.
- It helps to prevent the infinite loop.

## Tree recursion

This means making a recursive call more than once in your recursive case.

## Factorial of a Number

This is a recursive function that calculates the factorial of a number, implemented in JS:
```
function factorial(n) {
  if(n === 0) {
    return 1;
  } else {
    return n * factorial(n-1);
  }
}
```
