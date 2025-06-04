
# ✅ Two Sum IV - Input is a BST [[653](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/)]

## Problem Statement
Given the root of a Binary Search Tree and a target number `k`, return `true` if there exist two elements in the BST such that their sum is equal to the given target.

---

## Approaches

| Approach                              | Time Complexity | Space Complexity |
|-------------------------------------|-----------------|------------------|
| **DFS + HashSet**                   | O(n)            | O(n)             |
| **Inorder + Two Pointer**            | O(n)            | O(n)             |
| **For each node, search for (k - node.val)** | O(n log n)       | O(h)             |
| **BFS + HashSet**                    | O(n)            | O(n)             |

---

### Approach 1: DFS + HashSet  
- Traverse the tree using DFS (preorder, inorder, or postorder).
- Maintain a HashSet to store visited node values.
- For each node, check if `k - node.val` is in the set.
- If yes, return `true`.
- Else, add the current node's value to the set.
- If traversal ends with no match, return `false`.

**Time Complexity:** O(n)  
**Space Complexity:** O(n) for the HashSet and recursion stack.

---

### Approach 2: Inorder Traversal + Two Pointer  
- Perform an inorder traversal to get a sorted list of node values.
- Use two pointers, one at the start and one at the end of the list.
- Move pointers inward based on the sum compared to `k`.
- If sum matches `k`, return `true`.
- If no pairs found, return `false`.

**Time Complexity:** O(n)  
**Space Complexity:** O(n) for storing inorder traversal.

---

### Approach 3: For Each Node, Search (BST property)  
- For each node, search for `k - node.val` in the BST.
- Ensure not to count the node itself.
- Searching each node takes O(log n) on average, repeated for all nodes is O(n log n).

**Time Complexity:** O(n log n)  
**Space Complexity:** O(h) for recursion stack (height of tree).

---

### Approach 4: BFS + HashSet  
- Use BFS to traverse the tree level by level.
- For each node, check if `k - node.val` exists in the HashSet.
- If yes, return `true`.
- Otherwise, add current node value to the set.
- If BFS completes without finding the pair, return `false`.

**Time Complexity:** O(n)  
**Space Complexity:** O(n) for queue and HashSet.

---

## Summary

| Approach                           | Time Complexity | Space Complexity |
|----------------------------------|-----------------|------------------|
| DFS + HashSet                    | O(n)            | O(n)             |
| Inorder + Two Pointer             | O(n)            | O(n)             |
| For each node, BST search         | O(n log n)      | O(h)             |
| BFS + HashSet                    | O(n)            | O(n)             |

---

## Code Snippet (DFS + HashSet)

```java
class Solution {
    Set<Integer> set = new HashSet<>();
    int k;

    public boolean findTarget(TreeNode root, int k) {
        this.k = k;
        return dfs(root);
    }

    private boolean dfs(TreeNode node) {
        if (node == null) return false;
        if (set.contains(k - node.val)) return true;
        set.add(node.val);
        return dfs(node.left) || dfs(node.right);
    }
}
