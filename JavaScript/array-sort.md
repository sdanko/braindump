# Array Sort

Sort method is available in JavaScript arrays. This method sorts the elements of an array. It is in place operation, meaning that it transforms input array without auxiliary data structure and returns this array as a result.
Default sort order is ascending and method is executed this way:
1. Convert elements into strings
2. Compare sequences of UTF-16 code unit values

If compare function is provided, it is used to define the sort order. You can pass the compare function in multiple ways:
```
// Arrow function
sort((a, b) => { /* ... */ } )

// Compare function
sort(compareFn)

// Inline compare function
sort(function compareFn(a, b) { /* ... */ })
``` 

When compare function is supplied, all array elements are sorted according to the return value of compare function, All `undefined` elements are sorted to the end of the array(without no call to compare function).

| **compareFunction(a, b) return value** | **sort order**                 |
|----------------------------------------|--------------------------------|
| \>0                                    | sort b before a                |
| \<0                                    | sort a before b                |
| === 0                                  | keep original order of a and b |

Compare function has the following form:
```
function compare(a, b) {
  if (a is less than b by some ordering criterion) {
    return -1;
  }
  if (a is greater than b by the ordering criterion) {
    return 1;
  }
  // a must be equal to b
  return 0;
}
```

ECMAScript standard does not specify which sort algorithm should be used, so different browsers use different sorting algorithms. 
For example, Mozilla uses Merge sort and Chrome uses TimSort.

## `undefined` values in numeric comparison

Following example will work and all `undefined` values will be pushed to the end of an array:

```
const numbers = [4, 2, undefined, 5, undefined, 1, 3];
numbers.sort((a, b) => a - b);
console.log(numbers);

// [1, 2, 3, 4, 5, undefined, undefined]
```

But when comparing array of objects based on some object property it will not happen as expected:

```
const items = [
  { name: 'Edward', value: 21 },
  { name: 'Sharpe', value: 37 },
  { name: 'And', value: undefined },
  { name: 'The', value: -12 },
  { name: 'Zeros', value: 37 }
  { name: 'Magnetic', value: 13 }
];

items.sort(function (a, b) {
  return a.value - b.value;
});

console.log(items);

// 0: Object { name: "Edward", value: 21 }
// 1: Object { name: "Sharpe", value: 37 }
// 2: Object { name: "And", value: undefined }
// 3: Object { name: "The", value: -12 }
// 4: Object { name: "Magnetic", value: 13 }
// 5: Object { name: "Zeros", value: 37 }
```

In this case comparison function will try to subtract numeric values with `undefined`, which will return `NaN`.
This will result in element with `value: undefined` being unordered.

Resources:
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort
