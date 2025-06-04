## 📚  Problems Checklist

### 2 Search in a Binary Search Tree [[700](https://leetcode.com/problems/search-in-a-binary-search-tree/description/)]

-  **Recursive Approach** — Recursively search left or right subtree based on value.  
   TC: O(h) / SC: O(h)

-  **Iterative Approach** — Loop through tree nodes, move left or right based on value.  
   TC: O(h) / SC: O(1)

---
### 2 Find Min/Max in BST

-  **Iterative (Go Left for Min, Right for Max)** — Keep moving left for min or right for max until null.  
   TC: O(h) / SC: O(1)

-  **Recursive** — Recursively move left for min, right for max.  
   TC: O(h) / SC: O(h)

---
### 3 Ceil in a Binary Search Tree (Ceil = smallest value ≥ target)

-  **Iterative BST Traversal** — Traverse BST, move left if node ≥ target (update ans), else move right.  
   TC: O(h) / SC: O(1)

-  **Recursive BST Traversal** — Same logic as iterative but using recursion.  
   TC: O(h) / SC: O(h)

-  **Inorder Traversal + Linear Scan** — Do inorder traversal (sorted array), then find first element ≥ target.  
   TC: O(n) / SC: O(n)

---
### 4 Floor in a Binary Search Tree (Ceil = largest value <= target)

-  **Recursive Approach** — Traverse left/right based on node value vs target, track possible floor.  
   TC: O(h) / SC: O(h)

-  **Iterative Approach** — Similar to recursive, but with a loop to avoid recursion stack.  
   TC: O(h) / SC: O(1)

---



