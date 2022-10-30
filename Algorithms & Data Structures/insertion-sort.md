# Insertion Sort

Insertion sort is an in-place comparison-based sorting algorithm, that places an unsorted element at its
suitable place in each iteration.

## Implementation

This is the implementation in JS:

```
function insertionSort(array) {
  for(let i = 1; i < array.length; i++) {
    let key = array[i];
    let last = i - 1;
    
    while(last >= 0 && key < array[last]) {
      array[last + 1] = array[last];
      last = last - 1;
    }
    array[last + 1] = key;
  }
}
```

## Complexity

Average case complexity for Selection sort is O(n ^ 2).
