# Merge Sort

Merge sort is using the approach of divide and conquer.

Merge sort is using the following strategy:
- Split the array until the single element is left.
- Merge all the elements and sort them in that process.

## Implementation

This is the implementation in JS:

```
function mergeSort(array) {
	console.log(array);
	if(array.length === 1) {
  	return array;
  }
  
  const middle = Math.floor((array.length) / 2);
  const left = array.slice(0, middle);
  const right = array.slice(middle, array.length);
  
  const leftResult = mergeSort(left);
  const rightResult = mergeSort(right);
  
  return merge(leftResult, rightResult);
}

function merge(leftResult, rightResult) {
	console.log("Merge:", leftResult, rightResult);
	let result = [];
  let i, j, k;
  i = j = k = 0;
  
  while(i < leftResult.length && j < rightResult.length) {
  	if(leftResult[i] <= rightResult[j]) {
    	result[k] = leftResult[i];
      i += 1;
    } else {
    	result[k] = rightResult[j];
      j += 1;
    }
    k += 1;
  }
  
  while(i < leftResult.length) {
  	result[k] = leftResult[i];
    i += 1;
    k += 1;
  }
  
  while(j < rightResult.length) {
  	result[k] = rightResult[j];
    j += 1;
    k += 1;
  }
  
  return result;
}

console.log("Result:", mergeSort([4, 8, 3]));
```

## Complexity

In all cases complexity for Merge sort is n(log(n)).

Space complexity is O(n).
