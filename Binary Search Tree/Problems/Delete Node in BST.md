
### ✅ Delete Node in a BST [[450](https://leetcode.com/problems/delete-node-in-a-bst/description/)]

Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return the root node of the BST after deletion. It is guaranteed that the key exists in the BST.

Note: The deletion can be done in multiple valid ways as long as the BST property is maintained.

---

| Approach                    | Time Complexity | Space Complexity |
|-----------------------------|-----------------|------------------|
| **Recursive Deletion**       | O(h)            | O(h)             |
| **Iterative Deletion**       | O(h)            | O(1)             |

---

### Explanation:

1. **Recursive Deletion Approach:**  
   - Traverse the BST to find the node to delete.  
   - If node not found, return the unchanged root.  
   - If node found:  
     - If node is a leaf, delete it by returning null.  
     - If node has one child, replace node with that child.  
     - If node has two children, find the inorder successor (smallest node in the right subtree), replace node's value with successor's value, and delete the successor recursively.

2. **Iterative Deletion Approach:**  
   - Similar logic but use loops instead of recursion.  
   - More complex pointer manipulation but saves on recursive call stack.

---

### Sample Recursive Code (Java):

```java
class Solution {
    public TreeNode deleteNode(TreeNode root, int key) {
        if (root == null) return null;
        if (key < root.val) {
            root.left = deleteNode(root.left, key);
        } else if (key > root.val) {
            root.right = deleteNode(root.right, key);
        } else {
            // Node to be deleted found
            if (root.left == null) return root.right;
            else if (root.right == null) return root.left;
            else {
                // Node has two children
                TreeNode successor = findMin(root.right);
                root.val = successor.val;
                root.right = deleteNode(root.right, successor.val);
            }
        }
        return root;
    }
    
    private TreeNode findMin(TreeNode node) {
        while (node.left != null) node = node.left;
        return node;
    }
}

```

----------

### Correctness:

-   The BST property is maintained after deletion.
    
-   All cases (leaf, one child, two children) are handled correctly.
    

### Complexity:

-   Time: O(h), where h is the height of the tree, because we traverse from root to the target node.
    
-   Space: O(h) due to recursion stack in worst case (skewed tree), O(log n) on average.
    

----------

