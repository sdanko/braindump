# Hash tables

Biggest advantage of hash tables is complexity of O(1) for searching the elements.
When working with arrays, we define our own index positions for the elements. When working with hash tables,
they  utilize the property of the key and calculate the index position of the element by using the hash function.
By default, hash tables are implemented in the form of dynamic arrays.

## Collisions

Key can sometime refer to the same index position in the array. In that case collision happens and 
different solutions can be used to resolve the value. On of them is chaining: linked list is used to 
store the values that positioned on the same index. In this case accessing the value has the complexity
of O(n). Other solutions that can be used:
- Overflow areas
- Rehashing
- Quadratic probing
- Linear probing

## Complexities

| **Access**     | **Search**                        | **Insertion**                     | **Deletion**                      |
|----------------|-----------------------------------|-----------------------------------|-----------------------------------|
| Same as search | O(1) average case, O(n) edge case | O(1) average case, O(n) edge case | O(1) average case, O(n) edge case |
