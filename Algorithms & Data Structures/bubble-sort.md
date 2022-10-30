# Bubble Sort

Bubble sort is based on the idea of repeatedly comparing pairs of adjacent elements and then swapping
their positions if they exist in the wrong order.

The bubble sort gets its name because elements tend to move up into the correct order like bubbles 
rising to the surface.

## Implementation

This is the implementation in JS:
```
function bubbleSort(array) {
  for(let iter = 0; iter < array.length; iter++) {
    for(let i = 0; i < array.length - 1 - iter; i++) {
      if(array[i] > array[i + 1]) {
        [array[i], array[i + 1]] = [array[i + 1], array[i]];
      }
    }
  }
}
```

## Complexity

Average case complexity for Bubble sort is O(n ^ 2).
