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
### 5 Insert into a Binary Search Tree [[701](https://leetcode.com/problems/insert-into-a-binary-search-tree/description/)]

-  **Recursive Approach** — Traverse recursively to find insert position.  
   TC: O(h) / SC: O(h)

-  **Iterative Approach** — Use a loop to find insert position without recursion.  
   TC: O(h) / SC: O(1)

-  **Morris Traversal (Threaded BST)** — Not commonly used for insert, but possible for traversal with O(1) space (rare).  
   TC: O(n) / SC: O(1)

---
### 6 Delete Node in a BST [[450](https://leetcode.com/problems/delete-node-in-a-bst/description/)]

-  **Recursive Approach** — Recursively find the node, replace with inorder successor/predecessor if needed.  
   TC: O(h) / SC: O(h)

-  **Iterative Approach** — Use while loops to locate and delete node, handle cases for 0, 1, or 2 children.  
   TC: O(h) / SC: O(1)

---
### 7 Kth Smallest Element in a BST [[230](https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/)]

-  **Inorder Traversal (Recursive)** — Do inorder traversal (sorted order), decrement k, return kth value.  
   TC: O(h + k) / SC: O(h)

-  **Inorder Traversal (Iterative with Stack)** — Use stack to perform inorder iteratively, track k.  
   TC: O(h + k) / SC: O(h)

-  **Morris Inorder Traversal** — O(1) space inorder traversal using threaded binary tree technique.  
   TC: O(n) / SC: O(1)

-  **Augmented BST (Node Count Tracking)** — Store count of nodes in left subtree at each node for O(log n) access.  
   TC: O(h) / SC: O(1) (if counts maintained)

---

### 8 Lowest Common Ancestor of a Binary Search Tree [[235](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/)]

-  **Recursive BST Property** — Move left/right based on node values.  
   TC: O(h) / SC: O(h)

-  **Iterative BST Property** — Same logic as recursive, done iteratively.  
   TC: O(h) / SC: O(1)

-  **Path Finding + Compare Paths** — Find path from root to both nodes, then compare paths.  
   TC: O(n) / SC: O(n)

---
### 9 Validate Binary Search Tree [[98](https://leetcode.com/problems/validate-binary-search-tree/description/)]

-  **Recursive DFS with min/max limits** — Pass down valid range for each node.  
   TC: O(n) / SC: O(h)

-  **Inorder Traversal (Recursive)** — Check if inorder sequence is strictly increasing.  
   TC: O(n) / SC: O(h)

-  **Inorder Traversal (Iterative)** — Iterative stack-based inorder traversal to verify sorted order.  
   TC: O(n) / SC: O(h)

-  **Morris Inorder Traversal** — Threaded tree traversal for O(1) space inorder check.  
   TC: O(n) / SC: O(1)

---

### 10 Two Sum IV - Input is a BST [[653](https://leetcode.com/problems/two-sum-iv-input-is-a-bst/description/)]

-  **DFS + HashSet** — Traverse tree, store visited nodes in set, check complement.  
   TC: O(n) / SC: O(n)

-  **For each node, search complement in BST** — For each node, search BST for (k - node.val).  
   TC: O(n log n) average / SC: O(h)

-  **Inorder traversal + Two pointers** — Convert BST to sorted array, then use two-pointer approach.  
   TC: O(n) / SC: O(n)

-  **Iterative Inorder + Reverse Inorder Traversal (Two Iterators)** — Use two stacks to simulate forward and backward inorder traversals simultaneously.  
   TC: O(n) / SC: O(h)

---

### 11 Recover Binary Search Tree [[99](https://leetcode.com/problems/recover-binary-search-tree/description/)]
-  **Recursive Inorder DFS** — Track previous node, detect 2 anomalies, and swap values.Track first/middle/last/prev. Two cases 1-> Swapped not adjacent 2-> Not adjacent
TC: O(n) / SC: O(h)

-  **Iterative Inorder with Stack** — Same logic as recursive, using a stack for traversal.
TC: O(n) / SC: O(h)


-  **Morris Traversal (Threaded Binary Tree)** — Inorder traversal with O(1) space, find swapped nodes during traversal.
TC: O(n) / SC: O(1)
---

