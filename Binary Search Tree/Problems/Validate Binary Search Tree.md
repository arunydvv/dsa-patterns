
### ✅ Validate Binary Search Tree [[98](https://leetcode.com/problems/validate-binary-search-tree/)]

| Approach                          | Time Complexity | Space Complexity |
|----------------------------------|-----------------|------------------|
| **Inorder Traversal (Recursive)**| O(n)            | O(h)             |
| **Inorder Traversal (Iterative)**| O(n)            | O(h)             |
| **Divide & Conquer (Range Check)**| O(n)            | O(h)             |
| **Divide & Conquer (Using long min/max)** | O(n)    | O(h)             |

---

## Problem Statement

Given the root of a binary tree, determine if it is a valid binary search tree (BST).

A valid BST is defined as follows:
- The left subtree of a node contains only nodes with keys **less than** the node's key.
- The right subtree of a node contains only nodes with keys **greater than** the node's key.
- Both the left and right subtrees must also be binary search trees.

---

## Solutions

### 1. Inorder Traversal (Recursive)

**Idea:**  
Inorder traversal of a BST produces values in strictly ascending order. Traverse the tree inorder and check if the current value is greater than the previously visited value.

```java
class Solution {
    private TreeNode prev = null;
    
    public boolean isValidBST(TreeNode root) {
        return inorder(root);
    }
    
    private boolean inorder(TreeNode root) {
        if (root == null) return true;
        if (!inorder(root.left)) return false;
        if (prev != null && root.val <= prev.val) return false;
        prev = root;
        return inorder(root.right);
    }
}

```

**Time Complexity:** O(n) — visit each node once  
**Space Complexity:** O(h) — recursion stack, h is tree height

----------

### 2. Inorder Traversal (Iterative)

**Idea:**  
Same as recursive inorder but use an explicit stack to simulate the traversal.

```java
class Solution {
    public boolean isValidBST(TreeNode root) {
        Stack<TreeNode> stack = new Stack<>();
        TreeNode prev = null;
        TreeNode curr = root;
        
        while (curr != null || !stack.isEmpty()) {
            while (curr != null) {
                stack.push(curr);
                curr = curr.left;
            }
            curr = stack.pop();
            if (prev != null && curr.val <= prev.val) return false;
            prev = curr;
            curr = curr.right;
        }
        return true;
    }
}

```

**Time Complexity:** O(n)  
**Space Complexity:** O(h)

----------

### 3. Divide & Conquer (Range Check with Integer objects)

**Idea:**  
Recursively verify that each node’s value lies within the valid range allowed by BST rules.

```java
class Solution {
    public boolean isValidBST(TreeNode root) {
        return helper(root, null, null);
    }
    
    private boolean helper(TreeNode node, Integer lower, Integer upper) {
        if (node == null) return true;
        
        int val = node.val;
        if (lower != null && val <= lower) return false;
        if (upper != null && val >= upper) return false;
        
        if (!helper(node.left, lower, val)) return false;
        if (!helper(node.right, val, upper)) return false;
        
        return true;
    }
}

```

**Time Complexity:** O(n)  
**Space Complexity:** O(h)

----------

### 4. Divide & Conquer (Using `long` min/max to avoid overflow)

**Idea:**  
Use `long` to represent the allowed range to avoid potential integer overflow issues when the node values are at integer limits.

```java
class Solution {
    public boolean isValidBST(TreeNode root) {
        return validate(root, Long.MIN_VALUE, Long.MAX_VALUE);
    }
    
    private boolean validate(TreeNode node, long min, long max) {
        if (node == null) return true;
        
        if (node.val <= min || node.val >= max) return false;
        
        return validate(node.left, min, node.val) && validate(node.right, node.val, max);
    }
}

```

**Time Complexity:** O(n)  
**Space Complexity:** O(h)



----------

**This problem is a classic BST validation check and can be efficiently solved by inorder traversal or recursive range checking. The `long` min/max approach is safer when node values may approach integer boundaries.**