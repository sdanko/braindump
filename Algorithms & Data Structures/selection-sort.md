# Selection Sort

Selection sort is an algorithm that selects the smallest element from an unsorted list in each iteration
and places that element at the beginning of the unsorted list. It works the opposite way compared to Bubble
sort.

In every iteration minimum value is found and then the elements are swapped.

## Implementation

This is the implementation in JS:
```
function selectionSort(array) {
  for(let i = 0; i < array.length; i++) {
    let min = i;
    
    for(let j = i + 1; j < array.length; j++) {
    	if(array[j] < array[min]) {
      	min = j;
      }
    }
    
    [array[i], array[min]] = [array[min], array[i]];
  }
}
```

## Complexity

Average case complexity for Selection sort is O(n ^ 2).
