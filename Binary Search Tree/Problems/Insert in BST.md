
### ✅ Insert into a Binary Search Tree [[701](https://leetcode.com/problems/insert-into-a-binary-search-tree/)]

You are given the root node of a binary search tree (BST) and a value to insert into the tree. Return the root node of the BST after the insertion. It is guaranteed that the new value does not exist in the original BST.

Notice that there may exist multiple valid ways for the insertion, as long as the tree remains a BST after insertion. You can return any of them.

----------


| Approach               | Time Complexity | Space Complexity |
|------------------------|-----------------|------------------|
| **Recursive Insertion** | O(h)            | O(h)             |
| **Iterative Insertion** | O(h)            | O(1)             |


## Approach 1: Recursive Insertion

**Idea:**  
Use the BST property to find the correct position to insert the new value recursively.

-   If the current node is `null`, create a new node with the value.
    
-   If the value to insert is less than the current node's value, recurse into the left subtree.
    
-   Else, recurse into the right subtree.
    
-   Return the node after insertion.
    

**Code (Java):**

```java
class Solution {
    public TreeNode insertIntoBST(TreeNode root, int val) {
        if (root == null) return new TreeNode(val);

        if (val < root.val) {
            root.left = insertIntoBST(root.left, val);
        } else {
            root.right = insertIntoBST(root.right, val);
        }
        return root;
    }
}

```

**Time Complexity:** O(h), where h is the height of the BST.  
**Space Complexity:** O(h) due to recursion stack.

----------

## Approach 2: Iterative Insertion

**Idea:**  
Instead of recursion, use a loop to traverse the BST and find the correct place to insert the new node.

-   Maintain a pointer `curr` starting at the root.
    
-   Keep track of `parent` node.
    
-   Traverse left or right based on BST rules until you find a null position to insert.
    
-   Insert the new node as the child of `parent`.
    

**Code (Java):**

```java
class Solution {
    public TreeNode insertIntoBST(TreeNode root, int val) {
        TreeNode newNode = new TreeNode(val);
        if (root == null) return newNode;

        TreeNode curr = root, parent = null;
        while (curr != null) {
            parent = curr;
            if (val < curr.val) {
                curr = curr.left;
            } else {
                curr = curr.right;
            }
        }

        if (val < parent.val) {
            parent.left = newNode;
        } else {
            parent.right = newNode;
        }

        return root;
    }
}

```

**Time Complexity:** O(h)  
**Space Complexity:** O(1)

----------

### Notes:

-   Both approaches maintain the BST property.
    
-   The recursive method is cleaner but uses extra stack space.
    
-   The iterative method is more space-efficient.
    
-   **Multiple valid BSTs ** can be formed by different valid insertions, returning any is acceptable.
    

----------

_Happy coding!_