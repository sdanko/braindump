# Heaps

Four concepts that make a heap:
1. Structure arrangement(can be ascending or descending)
2. Complete BT
3. h = log n
4. Balanced BT

Can be implemented with array.

Compared to BT, greater values don't have to be on the left side.

Types:
- Max heap(maximum value at top, all children are lesser)
- Min heap(minimum value at top, all children are greater)

## Complexities

Not recommended for search operations.

| **Search** | **Insertion**                       | **Deletion** |
|------------|-------------------------------------|--------------|
| O(n)       | Best case O(n), worst case O(log n) | O(log n)     |
