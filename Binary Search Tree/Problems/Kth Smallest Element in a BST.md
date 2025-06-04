
## ✅ Kth Smallest Element in a BST [[230](https://leetcode.com/problems/kth-smallest-element-in-a-bst/)]

### 📑 Problem Description

Given the `root` of a binary search tree, and an integer `k`, return the `kth` smallest value (1-indexed) of all the values of the nodes in the tree.

----------

### 📊 Approaches, Time & Space Complexity


| Approach                          | Time Complexity | Space Complexity |
| --------------------------------- | --------------- | ---------------- |
| **Inorder Traversal (Recursive)** | O(N)            | O(H)             |
| **Inorder Traversal (Iterative)** | O(N)            | O(H)             |
| **Morris Traversal**              | O(N)            | O(1)             |

----------

### 📦 Solutions

#### 🔹 Approach 1: Inorder Traversal (Recursive)

```java
class Solution {
    int count = 0, ans = -1;
    public int kthSmallest(TreeNode root, int k) {
        inorder(root, k);
        return ans;
    }

    void inorder(TreeNode root, int k) {
        if (root == null) return;
        inorder(root.left, k);
        count++;
        if (count == k) ans = root.val;
        inorder(root.right, k);
    }
}

```

-   **Explanation:** Perform an inorder traversal since it visits nodes in sorted order for a BST. Keep a count of visited nodes. When count reaches k, store the value.
    

----------

#### 🔹 Approach 2: Inorder Traversal (Iterative with Stack)

```java
class Solution {
    public int kthSmallest(TreeNode root, int k) {
        Stack<TreeNode> st = new Stack<>();
        while (true) {
            while (root != null) {
                st.push(root);
                root = root.left;
            }
            root = st.pop();
            if (--k == 0) return root.val;
            root = root.right;
        }
    }
}

```

-   **Explanation:** Iterative inorder using a stack. Pop the k-th element visited.
    

----------

#### 🔹 Approach 3: Morris Traversal (Threaded Binary Tree)

```java
class Solution {
    public int kthSmallest(TreeNode root, int k) {
        int count = 0;
        int ans = -1;
        TreeNode curr = root;

        while (curr != null) {
            if (curr.left == null) {
                count++;
                if (count == k) ans = curr.val;
                curr = curr.right;
            } else {
                TreeNode pred = curr.left;
                while (pred.right != null && pred.right != curr) {
                    pred = pred.right;
                }
                if (pred.right == null) {
                    pred.right = curr;
                    curr = curr.left;
                } else {
                    pred.right = null;
                    count++;
                    if (count == k) ans = curr.val;
                    curr = curr.right;
                }
            }
        }
        return ans;
    }
}

```

-   **Explanation:** Morris traversal avoids recursion/stack by threading the tree temporarily. O(1) space.
    

----------
