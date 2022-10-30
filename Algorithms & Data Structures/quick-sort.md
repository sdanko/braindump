# Quick Sort

Main concept of quick sort: randomly select one element and get that element at right position.
This element is called pivot. Two pointers are used:
- Left pointer: first element after the pivot element
- Right pointer: last element

Steps(repeat until right pointer crossed the left pointer):
- If the value of the left pointer is greater than pivot and the value of the right pointer
is less than pivot, left and right pointers should be swapped.
- If left pointer is less than or equal to pivot, just move the pointer forward.
- If right pointer is greater than or equal to pivot, just move the pointer backward.
- Once the right pointer cross the left pointer, swap right pointer with pivot.
- After this, apply the same steps to the left and right side elements of the pivot element(there will
be two lists)

## Implementation

This is the implementation in JS:

```
function quickSort(array) {
  qsHelper(array, 0, array.length - 1);
  
  return array;
}

function qsHelper(array, start, end) {
	if(start >= end) {
  	return;
  }
  
  const pivot = start;
  let left = start + 1;
  let right = end;
  
  while(right >= left) {
  	if(array[left] > array[pivot] && array[right] < array[pivot]) {
    	[array[left], array[right]] = [array[right], array[left]];
    }
    
    if(array[left] <= array[pivot]) {
    	left += 1;
    }
    
    if(array[right] >= array[pivot]) {
    	right -= 1;
    }
  }
  
  [array[pivot], array[right]] = [array[right], array[pivot]];
  
  qsHelper(array, start, right - 1);
  qsHelper(array, right + 1, end);
}
```

## Complexity

Average case and best case complexity for Quick sort is n(log(n)).

Worst case is when everything is already sorted: n^2.
