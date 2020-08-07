# Morris Traversal
## Why
Morris Traversal provides us with a approach to traverse binary tree in O(1) space.

## How
Before we even start traverse the left child tree of root, we link the right-most node to root. 

Since the right-most node is the last node we will be visiting in an inorder traverse, this link can lead us back to root after finished exploring.

This applies to all the subtrees.

## Details
1. If root does not have left child, just visit root.right.

2. If there is root.left, find the right-most child node of root.left.

**Note:** It is possible we have already connect the right-most node to the root. So, when we are looking for the right-most node, the termination conditions should be null and not root.

If the right-most node has right child, which is the root, then we should break the link and visit root.right.

if the right-most node has not right child, connect it to root. Then visit root.left.

## Example
```
while (root != null) {
    if (root.left != null) {
        predecessor = root.left;
        while (predecessor.right != null && predecessor.right != root) {
            predecessor = predecessor.right;
        }
        
        if (predecessor.right == null) {
            predecessor.right = root;
            root = root.left;
        }
        else {
            if (pred != null && root.val < pred.val) {
                y = root;
                if (x == null) {
                    x = pred;
                }
            }
            pred = root;

            predecessor.right = null;
            root = root.right;
        }
    }
    else {
        if (pred != null && root.val < pred.val) {
            y = root;
            if (x == null) {
                x = pred;
            }
        }
        pred = root;
        root = root.right;
    }
}
```