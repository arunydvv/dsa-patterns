
### ✅ Lowest Common Ancestor of a Binary Search Tree [[235](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)]

You are given the root of a binary search tree (BST), and two values `p` and `q`. Find the lowest common ancestor (LCA) of the two nodes.

The **lowest common ancestor** is defined between two nodes `p` and `q` as the lowest node in BST that has both `p` and `q` as descendants (a node can be a descendant of itself).

---

### 📌 Approaches  

| Approach                     | Time Complexity | Space Complexity |
|:-----------------------------|:----------------|:-----------------|
| **Recursive (BST property-based)** | O(h)            | O(h)             |
| **Iterative (BST property-based)** | O(h)            | O(1)             |

---

### 📖 Approach Explanations  

#### 📝 Recursive (BST property-based)
- Leverage the BST property:  
  - If both `p` and `q` are smaller than the current node, go left.  
  - If both are greater, go right.  
  - If they split or one equals the current node, that’s the LCA.
- Base case recursion.

#### 📝 Iterative (BST property-based)
- Same logic as recursive, but use a `while` loop to traverse without call stack overhead.
- Stop when you find the split point or when one value matches.

---

### 💡 Code  

#### ✅ Recursive  

```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if (root.val > p.val && root.val > q.val) 
            return lowestCommonAncestor(root.left, p, q);
        else if (root.val < p.val && root.val < q.val) 
            return lowestCommonAncestor(root.right, p, q);
        else 
            return root;
    }
}

```

#### ✅ Iterative

```java
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        while (root != null) {
            if (root.val > p.val && root.val > q.val)
                root = root.left;
            else if (root.val < p.val && root.val < q.val)
                root = root.right;
            else
                return root;
        }
        return null;
    }
}

```

----------

### 📊 Correctness & Complexity

-   **Correctness**: Guaranteed by BST property — at each node, deciding direction based on p & q positions ensures LCA is correctly identified.
    
-   **Time Complexity**: O(h), where h is the height of the BST (O(log n) for balanced BST)
    
-   **Space Complexity**:
    
    -   O(h) for recursive stack
        
    -   O(1) for iterative solution
        

----------

