# Array Reduce

Reduce method is available in JavaScript arrays. It should not be confused with reducers in Redux state management, but it is a similar concept. This is the signature of the method:

```
arr.reduce(callback, initialValue);
``` 

The first argument is a callback function which is often referred to as a reducer. You can also pass optional initial value for the second argument. Callback function is called for every element in the array and the result from every call is accumulated and returned. This function has the following signature:

```
callbackFn(previousValue, currentValue, currentIndex, array)
``` 

- `previousValue` - value from the previous call of the callback function. On the first call, the `initialValue` is the `previousValue`, if `initialValue` is provided. Otherwise, its value is `array[0]`. Also, it is usually referred to as `accumulator`.
- `currentValue` - the value of the current element for which callback function is called. On the first call, its value is `array[0]` if you provide `initialValue` or `array[1]` otherwise.
- `currentIndex` - the index of the `currentValue` in the array. On the first call, it’s 0 if you provide `initialValue` or 1 otherwise.
- `array` - the array that the callback function is looping through.

Classical use case is when we want to sum up all the numbers in the array:

```
const numbers = [5, 10, 15];

const reducer = (accumulator, item) => {
  return accumulator + item;
};

const total = numbers.reduce(reducer);
``` 

Reduce method can be used for other useful thing as flattening arrays, changing object structure and cloning objects. This is how we can use it for cloning:

```
const obj = { a: 1, b: 2 };

const shallowClone = Object.keys(obj).reduce(
  (acc, key) => {
    acc[key] = obj[key];
    return acc;
  },
  {}
);
``` 

In this case we're returning an object from every reduce method call. Since objects are passed by reference, this means we will deal with the same object in every method call. In every iteration we add the properties from the original object and in the end we end up with the object that has the identical properties that is returned from the final call.

Resources:
- https://www.javascripttutorial.net/javascript-array-reduce/
- https://www.digitalocean.com/community/tutorials/js-finally-understand-reduce
