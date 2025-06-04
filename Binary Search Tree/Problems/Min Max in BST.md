
### ✅ Min Max in a Binary Search Tree

Given the root of a Binary Search Tree (BST), find the minimum and maximum values stored in the BST.

---

| Approach               | Time Complexity | Space Complexity |
|------------------------|-----------------|------------------|
| **Find Min by Leftmost Node**  | O(h)            | O(1)             |
| **Find Max by Rightmost Node** | O(h)            | O(1)             |

---

## Approach 1: Find Minimum Value

**Idea:**  
In a BST, the minimum value is located at the leftmost node.  
- Start from root.  
- Keep moving to the left child until you reach a node with no left child.  
- That node contains the minimum value.

**Code (Java):**
```java
public int findMin(TreeNode root) {
    if (root == null) throw new IllegalArgumentException("Tree is empty");
    TreeNode curr = root;
    while (curr.left != null) {
        curr = curr.left;
    }
    return curr.val;
}

```

**Time Complexity:** O(h), where h is the height of the BST.  
**Space Complexity:** O(1)

----------

## Approach 2: Find Maximum Value

**Idea:**  
In a BST, the maximum value is located at the rightmost node.

-   Start from root.
    
-   Keep moving to the right child until you reach a node with no right child.
    
-   That node contains the maximum value.
    

**Code (Java):**

```java
public int findMax(TreeNode root) {
    if (root == null) throw new IllegalArgumentException("Tree is empty");
    TreeNode curr = root;
    while (curr.right != null) {
        curr = curr.right;
    }
    return curr.val;
}

```

**Time Complexity:** O(h)  
**Space Complexity:** O(1)

----------

### Notes:

-   Both operations take advantage of BST properties.
    
-   This is the most efficient way to get min and max in a BST.
    
-   Recursive approaches are possible but less space efficient.
    

----------

_Happy coding!_