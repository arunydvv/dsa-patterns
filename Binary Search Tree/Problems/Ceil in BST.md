

### ✅ Ceil in a Binary Search Tree

**Problem Statement:**  
Given a Binary Search Tree (BST) and a target value `x`, find the *ceil* of `x` in the BST.  
The *ceil* is the smallest element in the BST that is **greater than or equal** to `x`.  
If no such element exists, return -1 or indicate no ceil found.

---

| Approach               | Time Complexity | Space Complexity |
|------------------------|-----------------|------------------|
| **Iterative Search**    | O(h)            | O(1)             |
| **Recursive Search**    | O(h)            | O(h)             |

---

## Approach 1: Iterative Search

**Idea:**  
- Initialize a variable `ceil` as -1 (or null).  
- Start from the root and traverse down the BST:  
  - If `node.val == x`, then `node.val` is the ceil.  
  - If `node.val < x`, move to the right subtree (values greater than current).  
  - Else (`node.val > x`), update `ceil = node.val` and move to left subtree to find a smaller ceil if possible.  
- Return `ceil`.

**Code (Java):**
```java
public int findCeil(TreeNode root, int x) {
    int ceil = -1;
    TreeNode curr = root;
    while (curr != null) {
        if (curr.val == x) {
            return curr.val;
        }
        if (curr.val < x) {
            curr = curr.right;
        } else {
            ceil = curr.val;
            curr = curr.left;
        }
    }
    return ceil;
}

```

**Time Complexity:** O(h), where h is height of the BST.  
**Space Complexity:** O(1).

----------

## Approach 2: Recursive Search

**Idea:**

-   Recursively check the root:
    
    -   If root is null, return -1.
        
    -   If root.val == x, return root.val.
        
    -   If root.val < x, recurse right.
        
    -   Else recurse left and if left recursion returns -1, return root.val; else return left recursion result.
        

**Code (Java):**

```java
public int findCeil(TreeNode root, int x) {
    if (root == null) return -1;
    if (root.val == x) return root.val;

    if (root.val < x) {
        return findCeil(root.right, x);
    }

    int leftCeil = findCeil(root.left, x);
    return (leftCeil >= x) ? leftCeil : root.val;
}

```

**Time Complexity:** O(h)  
**Space Complexity:** O(h) due to recursion stack.

----------

### Notes:

-   Ceil is useful in many BST-based algorithms.
    
-   If no node value >= x, the function returns -1 indicating no ceil found.
    
-   Both approaches leverage BST property for efficient search.
    

----------

_Happy coding!_

