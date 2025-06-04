

### ✅ Search in a Binary Search Tree [[700](https://leetcode.com/problems/search-in-a-binary-search-tree/)]

Given the root node of a binary search tree (BST) and a value. You need to find the node in the BST that the node's value equals the given value. Return the subtree rooted with that node. If such node does not exist, return null.

---

| Approach           | Time Complexity | Space Complexity |
|--------------------|-----------------|------------------|
| **Recursive Search** | O(h)            | O(h)             |
| **Iterative Search** | O(h)            | O(1)             |

---

## Approach 1: Recursive Search

**Idea:**  
Use the BST property to decide whether to search left or right subtree recursively.  
- If current node is `null` or equals the target value, return the node.  
- If target is less than current node's value, recurse into left subtree.  
- Else, recurse into right subtree.

**Code (Java):**
```java
class Solution {
    public TreeNode searchBST(TreeNode root, int val) {
        if (root == null || root.val == val) {
            return root;
        }

        if (val < root.val) {
            return searchBST(root.left, val);
        } else {
            return searchBST(root.right, val);
        }
    }
}

```

**Time Complexity:** O(h), where h is the height of the BST.  
**Space Complexity:** O(h) due to recursion stack.

----------

## Approach 2: Iterative Search

**Idea:**  
Use a loop to traverse the BST:

-   Start from root, while current node is not `null` and value does not match,
    
-   Move left if target value < current node value, else right.
    
-   Return node if found, else `null`.
    

**Code (Java):**

```java
class Solution {
    public TreeNode searchBST(TreeNode root, int val) {
        TreeNode curr = root;
        while (curr != null && curr.val != val) {
            if (val < curr.val) {
                curr = curr.left;
            } else {
                curr = curr.right;
            }
        }
        return curr;
    }
}

```

**Time Complexity:** O(h)  
**Space Complexity:** O(1)

----------

### Notes:

-   Both methods utilize BST properties to search efficiently.
    
-   Recursive method uses extra stack space.
    
-   Iterative method is more space efficient.
    
-   Returns subtree rooted at found node or null if not found.
    

----------

_Happy coding!_