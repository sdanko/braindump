# Binary Search

When implementing binary search, the input elements have to be sorted.

In binary search, you first calculate the middle element. Then you compare is the middle element the one
that you are searching for. If yes, return it. If no, check is the element we are searching for smaller or
greater than the middle element. If it is smaller, continue searching on the left side, and if larger,
continue searching on the right side. Do these operations until the element is found.

Binary search is implemented using left and right pointers.

## Complexity 

Complexity for binary search is O(log n).

Best case: O(1)
Worst case: log(n)
Average case: log(n)

## Implementation

In JS:

```
function binarySearch(array, target) {
  let left = 0;
  let right = array.length - 1;
  
  while(left <= right) {
    let middle = Math.floor((left + right) / 2);
    let middleElement = array[middle];
    
    if(target === middleElement) {
      return middle;
    } else if(target < middleElement) {
      right = middle - 1;
    } else {
      left = middle + 1;
    }
  }
  
  return -1;
}
```

### Recursive implementation

```
function binarySearch(array, target) {
  let left = 0;
  let right = array.length - 1;
  return helper(array, target, left, right);
}

function helper(array, target, left, right) {
  if(left > right) {
  	return -1;
  }
  
  const middle = Math.floor((left + right) / 2);
  const middleElement = array[middle];
  
  if(target === middleElement) {
  	return middle;
  } else if(target < middleElement) {
  	right = middle - 1;
    return helper(array, target, left, right);
  } else  {
  	left = middle + 1;
    return helper(array, target, left, right);
  }
}
```
