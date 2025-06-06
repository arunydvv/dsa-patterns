
# ✅ Inorder Successor/Predecessor in BST [[510](https://leetcode.com/problems/inorder-successor-in-bst/) & [285](https://leetcode.com/problems/inorder-successor-in-bst/)]

## 📖 Problem  
Given a binary search tree (BST) and a node in it, find the in-order successor and in-order predecessor of that node in the BST.

- **Successor**: Node with the smallest key greater than the given node.
- **Predecessor**: Node with the largest key smaller than the given node.

---

## ✅ Approaches, Time and Space Complexity  

| Approach                            | Time Complexity | Space Complexity |
|:------------------------------------|:----------------|:-----------------|
| **Recursive Search (BST Property)** | O(h)             | O(h) (recursion stack) |
| **Iterative Search (Using BST Property)** | O(h)        | O(1)             |
| **Inorder Traversal with flag**     | O(n)             | O(h)             |

---

## 📌 Approach Details  

### 📌 Approach 1: Recursive Search Using BST Property  
- If current node value > target, go left and update successor.  
- If current node value < target, go right and update predecessor.  
- Recursively traverse down the tree.

**TC:** O(h) | **SC:** O(h)

---

### 📌 Approach 2: Iterative Search (Optimized BST Property)  
- Use a while loop, moving left/right based on comparisons.
- Keep track of possible successor/predecessor during traversal.

**TC:** O(h) | **SC:** O(1)

---

### 📌 Approach 3: Inorder Traversal with Flag  
- Do an inorder traversal.
- Track the previous node and set it as predecessor.
- When you find the target node, the next node in inorder is its successor.

**TC:** O(n) | **SC:** O(h)

---

## ✅ Code (Java — Iterative Successor Example)

```java
public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
    TreeNode succ = null;
    while (root != null) {
        if (p.val < root.val) {
            succ = root;
            root = root.left;
        } else {
            root = root.right;
        }
    }
    return succ;
}

```

----------

## 📊 Notes

-   Best optimized solution is **Approach 2** for both successor and predecessor.
    
-   For skewed trees, time complexity becomes O(n).
    

----------

## 📚 Related

-   [✅ 510. Inorder Successor in BST II](https://leetcode.com/problems/inorder-successor-in-bst-ii/)
    
-   [✅ 285. Inorder Successor in BST](https://leetcode.com/problems/inorder-successor-in-bst/)
    
-   [✅ 173. BST Iterator](https://leetcode.com/problems/binary-search-tree-iterator/)
    

----------



