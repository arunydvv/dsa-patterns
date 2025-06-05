
# ✅ Recover Binary Search Tree [[99](https://leetcode.com/problems/recover-binary-search-tree/)]

## Problem Statement  
You are given the root of a binary search tree (BST), where exactly two nodes of the tree were swapped by mistake. Recover the tree without changing its structure.

---

## Approaches

| Approach | Time Complexity | Space Complexity |
|----------|-----------------|------------------|
| **Inorder Traversal + Sorting** | O(n log n) | O(n) |
| **Inorder Traversal + Detecting swapped nodes** | O(n) | O(n) |
| **Morris Inorder Traversal (O(1) space)** | O(n) | O(1) |

---

### Approach 1: Inorder Traversal + Sorting  
- Perform an inorder traversal of the BST to get nodes in an array.  
- Sort the array of values.  
- Reassign the sorted values back to the nodes in inorder fashion.  

**Time:** O(n log n) due to sorting  
**Space:** O(n) to store nodes

---

### Approach 2: Inorder Traversal + Detecting Swapped Nodes  
- Perform inorder traversal and keep track of previous node.  
- Identify two nodes that are swapped by finding where the BST property breaks.  
- Swap the values of these two nodes to fix the tree.  

**Time:** O(n)  
**Space:** O(n) due to recursion stack (worst case)

---

### Approach 3: Morris Inorder Traversal (O(1) space)  
- Use Morris traversal to do inorder traversal without recursion or stack.  
- Detect the two swapped nodes as in Approach 2.  
- Swap their values to recover the BST.  

**Time:** O(n)  
**Space:** O(1)

---

## Code (Approach 2: Inorder Traversal + Detecting Swapped Nodes)

```java
class Solution {
    TreeNode first = null, second = null, prev = new TreeNode(Integer.MIN_VALUE);

    public void recoverTree(TreeNode root) {
        inorder(root);
        // Swap values of first and second nodes
        int temp = first.val;
        first.val = second.val;
        second.val = temp;
    }

    private void inorder(TreeNode root) {
        if (root == null) return;

        inorder(root.left);

        // If previous node's value is greater than current node's value, violation found
        if (prev.val > root.val) {
            if (first == null) first = prev;
            second = root;
        }
        prev = root;

        inorder(root.right);
    }
}

```

----------

## Explanation:

-   Inorder traversal of BST yields a sorted sequence.
    
-   The two swapped nodes disrupt the sorted order.
    
-   By detecting the first and second nodes where the order breaks, we can swap them back.
    
-   Using a previous pointer (`prev`) helps track the last visited node during inorder traversal.
    

----------

## Correctness

-   The approach correctly identifies the two nodes that were swapped.
    
-   Swapping their values restores the BST property without altering the structure.
    

----------

## Complexity

-   Time: O(n), where n is the number of nodes in the BST.
    
-   Space: O(h), where h is the height of the tree due to recursion stack (O(n) in worst case).
    

----------

_This solution is widely accepted and runs efficiently for large BSTs._

----------