# Trees

Tree is a form of a graph. It has a hierarchical structure. Elements of the tree are called nodes.

- Root node: node from which the tree structure begins.
- Parent and child relationships: every node can have a parent or child node relationship.
- Levels: when expanding the tree with new child nodes we are increasing the levels of the structure.
- Edge: connection between the elements. They have a direction. In trees, the direction is always from
the parent node to child node.
- Siblings: nodes with the same parent are referred to as siblings.
- Leaf node: the last element which does not have any child is known as leaf node.
- Inner node: any node that is not leaf node.

Node can only have one parent, but it can have multiple children. In tree, we are moving in top to bottom
direction.

## Depth

The depth of any node is defined as the length of the path from the root node to that particular node.

## Height

The height of any node is the number of edges from that node to the deepest leaf. In other words, it is
the longest path from that node to leaf node.

```
height of tree = height of roote node
```
