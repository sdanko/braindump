# Array

Common operations: 
- Access
- Search
- Insert
- Delete

## Complexities

| **Access** | **Search**  | **Insertion** | **Deletion** |
|------------|-------------|---------------|--------------|
| O(1)       | O(n)        | O(1)          | O(n)         |

## Types

There are two types of arrays:
- Static: Fixed number of memory slots(used in Java, C, C++).
- Dynamic: Flexible number of memory slots(used in Python, JavaScript).

In dynamic arrays, our system allocates extra number of memory slots then required. The number of memory slots
that are allocated is calculated the following way: use the smallest power of 2 that is just greater or equal
to the length of our array. This can be visualized when looking at the table with power of 2:

```
2^1 = 2
2^2 = 4
2^3 = 8
2^4 = 16
2^5 = 32
2^6 = 64
2^7 = 128
```

For example, when you have 3 elements in the array, array is going to reserve space for 4 elements, since 3
is closest to number 4 found in the table of power of 2. For array with 4 elements, 4 slots will be reserved 
and so on.

Inserting values in static array requires copying complete array into a new position every time.
Complexity is different for insertion in case of dynamic arrays:
- **O(1)** - in most cases
- **O(n)** - edge cases
