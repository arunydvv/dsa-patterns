
## 📚 LeetCode Problems Checklist

### ✅ Binary Tree Postorder Traversal [[145](https://leetcode.com/problems/binary-tree-postorder-traversal/description/)]

- **Recursive Approach** — Simple DFS using recursion.  
   TC: O(n) / SC: O(h)

- **Iterative with Stack (2 stacks)** — Use two stacks to mimic postorder.  
   TC: O(n) / SC: O(n)

- **Iterative with Stack (1 stack)** — Track previously visited node.  
   TC: O(n) / SC: O(n)

- **Morris Traversal (Threaded Binary Tree)** — O(1) space using temporary links.  
   TC: O(n) / SC: O(1)

---

### ✅ Binary Tree Preorder Traversal [[144](https://leetcode.com/problems/binary-tree-preorder-traversal/description/)]

- **Recursive Approach** — Simple DFS using recursion.  
   TC: O(n) / SC: O(h)

- **Iterative with Stack** — Use stack to simulate recursion.  
   TC: O(n) / SC: O(n)

- **Morris Traversal (Threaded Binary Tree)** — O(1) space using temporary links.  
   TC: O(n) / SC: O(1)

---

### ✅ Binary Tree Inorder Traversal [[94](https://leetcode.com/problems/binary-tree-inorder-traversal/)]

- **Recursive Approach** — Simple DFS using recursion.  
   TC: O(n) / SC: O(h)

- **Iterative with Stack** — Use stack to simulate recursion.  
   TC: O(n) / SC: O(n)

- **Morris Traversal (Threaded Binary Tree)** — O(1) space using temporary links.  
   TC: O(n) / SC: O(1)

---

### ✅ Binary Tree Level Order Traversal [[102](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)]

- **BFS with Queue** — Standard level-by-level traversal using a queue.  
   TC: O(n) / SC: O(n)

- **DFS with Level Tracking** — Use recursion, passing level as parameter.  
   TC: O(n) / SC: O(h)

---

### ✅ N-ary Tree Level Order Traversal [[429](https://leetcode.com/problems/n-ary-tree-level-order-traversal/description/)]

- **BFS with Queue** — Standard level-order traversal using queue.  
   TC: O(n) / SC: O(n)

---

### ✅ Minimum Number of Operations to Sort a Binary Tree by Level [[2471](https://leetcode.com/problems/minimum-number-of-operations-to-sort-a-binary-tree-by-level/description/)]

- **Level Order Traversal + Min Swaps Calculation** — Traverse each level, count min swaps to sort it.  
   TC: O(n log n) / SC: O(n)

---

### ✅ Kth Largest Sum in a Binary Tree [[2583](https://leetcode.com/problems/kth-largest-sum-in-a-binary-tree/)]

- **Level Order Traversal (BFS + Max-Heap)** — Collect level sums, push to max-heap, pop k-1 times, then get top.  
   TC: O(n log n) / SC: O(n)

---

### ✅ Maximum Depth/Height of Binary Tree [[104](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/)]

- **Recursive DFS** — Traverse left & right, take max depth.  
   TC: O(n) / SC: O(h)

- **Iterative DFS (with Stack)** — Use stack to track nodes and depth.  
   TC: O(n) / SC: O(h)

- **Iterative BFS (with Queue)** — Level order traversal, track levels.  
   TC: O(n) / SC: O(w) (w = max width of tree)

---

### ✅ Balanced Binary Tree [[110](https://leetcode.com/problems/balanced-binary-tree/description/)]

- **Recursive (Bottom-up)** — Check height & balance while unwinding recursion.  
   TC: O(n) / SC: O(h)

- **Recursive (Top-down)** — Check balance at each node, compute height separately.  
   TC: O(n²) / SC: O(h)

---

### ✅ Diameter of Binary Tree [[543](https://leetcode.com/problems/diameter-of-binary-tree/description/)]

- **Recursive (Bottom-up)** — Compute height while updating the maximum diameter during recursion unwind.  
   TC: O(n) / SC: O(h)

- **Recursive (Top-down)** — For each node, compute height of left and right subtrees separately to calculate diameter.  
   TC: O(n²) / SC: O(h)

---

### ✅ Binary Tree Maximum Path Sum [[124](https://leetcode.com/problems/binary-tree-maximum-path-sum/description/)]

- **Recursive DFS with Global Max** — Track max path sum including and excluding each node.  
   TC: O(n) / SC: O(h)

- **Divide and Conquer** — Compute max path sums from left and right subtrees, update global max.  
   TC: O(n) / SC: O(h)

---

### ✅ Same Tree [[100](https://leetcode.com/problems/same-tree/description/)]

- **Recursive DFS** — Compare nodes recursively.  
   TC: O(n) / SC: O(h)

- **Iterative BFS** — Use queue to compare level-wise.  
   TC: O(n) / SC: O(n)

- **Iterative DFS** — Use stack to compare nodes.  
   TC: O(n) / SC: O(n)

---

### ✅ Invert Binary Tree [[226](https://leetcode.com/problems/invert-binary-tree/)]

- **Recursive Approach** — Swap left and right subtrees via DFS recursion.  
   TC: O(n) / SC: O(h)

- **Iterative Approach** — Use a queue or stack to swap nodes level-by-level.  
   TC: O(n) / SC: O(n)

---
