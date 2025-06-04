## 📚  Problems Checklist

### 1 Binary Tree Postorder Traversal [[145](https://leetcode.com/problems/binary-tree-postorder-traversal/description/)]

- **Recursive Approach** — Simple DFS using recursion.  
   TC: O(n) / SC: O(h)

- **Iterative with Stack (2 stacks)** — Use two stacks to mimic postorder.  
   TC: O(n) / SC: O(n)

- **Iterative with Stack (1 stack)** — Track previously visited node.  
   TC: O(n) / SC: O(n)

- **Morris Traversal (Threaded Binary Tree)** — O(1) space using temporary links.  
   TC: O(n) / SC: O(1)

---

### 2 Binary Tree Preorder Traversal [[144](https://leetcode.com/problems/binary-tree-preorder-traversal/description/)]

- **Recursive Approach** — Simple DFS using recursion.  
   TC: O(n) / SC: O(h)

- **Iterative with Stack** — Use stack to simulate recursion.  
   TC: O(n) / SC: O(n)

- **Morris Traversal (Threaded Binary Tree)** — O(1) space using temporary links.  
   TC: O(n) / SC: O(1)

---

### 3 Binary Tree Inorder Traversal [[94](https://leetcode.com/problems/binary-tree-inorder-traversal/)]

- **Recursive Approach** — Simple DFS using recursion.  
   TC: O(n) / SC: O(h)

- **Iterative with Stack** — Use stack to simulate recursion.  
   TC: O(n) / SC: O(n)

- **Morris Traversal (Threaded Binary Tree)** — O(1) space using temporary links.  
   TC: O(n) / SC: O(1)

---

### 4 Binary Tree Level Order Traversal [[102](https://leetcode.com/problems/binary-tree-level-order-traversal/description/)]

- **BFS with Queue** — Standard level-by-level traversal using a queue.  
   TC: O(n) / SC: O(n)

- **DFS with Level Tracking** — Use recursion, passing level as parameter.  
   TC: O(n) / SC: O(h)

---

### 5 N-ary Tree Level Order Traversal [[429](https://leetcode.com/problems/n-ary-tree-level-order-traversal/description/)]

- **BFS with Queue** — Standard level-order traversal using queue.  
   TC: O(n) / SC: O(n)

---

### 6 Minimum Number of Operations to Sort a Binary Tree by Level [[2471](https://leetcode.com/problems/minimum-number-of-operations-to-sort-a-binary-tree-by-level/description/)]

- **Level Order Traversal + Min Swaps Calculation** — Traverse each level, count min swaps to sort it.  
   TC: O(n log n) / SC: O(n)

---

### 7 Kth Largest Sum in a Binary Tree [[2583](https://leetcode.com/problems/kth-largest-sum-in-a-binary-tree/)]

- **Level Order Traversal (BFS + Max-Heap)** — Collect level sums, push to max-heap, pop k-1 times, then get top.  
   TC: O(n log n) / SC: O(n)

---

### 8 Maximum Depth/Height of Binary Tree [[104](https://leetcode.com/problems/maximum-depth-of-binary-tree/description/)]

- **Recursive DFS** — Traverse left & right, take max depth.  
   TC: O(n) / SC: O(h)

- **Iterative DFS (with Stack)** — Use stack to track nodes and depth.  
   TC: O(n) / SC: O(h)

- **Iterative BFS (with Queue)** — Level order traversal, track levels.  
   TC: O(n) / SC: O(w) (w = max width of tree)

---

### 9 Balanced Binary Tree [[110](https://leetcode.com/problems/balanced-binary-tree/description/)]

- **Recursive (Bottom-up)** — Check height & balance while unwinding recursion.  
   TC: O(n) / SC: O(h)

- **Recursive (Top-down)** — Check balance at each node, compute height separately.  
   TC: O(n²) / SC: O(h)

---

### 10 Diameter of Binary Tree [[543](https://leetcode.com/problems/diameter-of-binary-tree/description/)]

- **Recursive (Bottom-up)** — Compute height while updating the maximum diameter during recursion unwind.  
   TC: O(n) / SC: O(h)

- **Recursive (Top-down)** — For each node, compute height of left and right subtrees separately to calculate diameter.  
   TC: O(n²) / SC: O(h)

---

### 11 Binary Tree Maximum Path Sum [[124](https://leetcode.com/problems/binary-tree-maximum-path-sum/description/)]

- **Recursive DFS with Global Max** — Track max path sum including and excluding each node.  
   TC: O(n) / SC: O(h)

- **Divide and Conquer** — Compute max path sums from left and right subtrees, update global max.  
   TC: O(n) / SC: O(h)

---

### 12 Same Tree [[100](https://leetcode.com/problems/same-tree/description/)]

- **Recursive DFS** — Compare nodes recursively.  
   TC: O(n) / SC: O(h)

- **Iterative BFS** — Use queue to compare level-wise.  
   TC: O(n) / SC: O(n)

- **Iterative DFS** — Use stack to compare nodes.  
   TC: O(n) / SC: O(n)

---

### 13 Invert Binary Tree [[226](https://leetcode.com/problems/invert-binary-tree/)]

- **Recursive Approach** — Swap left and right subtrees via DFS recursion.  
   TC: O(n) / SC: O(h)

- **Iterative Approach** — Use a queue or stack to swap nodes level-by-level.  
   TC: O(n) / SC: O(n)

---

### 14 Binary Tree Zigzag Level Order Traversal [[103](https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/)]

- **BFS with deque** — Use queue and reverse order every alternate level.  
   TC: O(n) / SC: O(n)

- **DFS with level tracking** — Traverse preorder, add nodes in zigzag by level.  
   TC: O(n) / SC: O(h)

---

### 15 Symmetric Tree [[101](https://leetcode.com/problems/symmetric-tree/description/)]

- **Recursive Approach** — Compare left & right subtrees recursively.  
   TC: O(n) / SC: O(h)

- **Iterative Approach** — Use queue to compare nodes level-wise.  
   TC: O(n) / SC: O(n)

---

### 16 Boundary of Binary Tree [[545](https://leetcode.com/problems/boundary-of-binary-tree/description/)]

- **DFS Traversal** — Traverse left boundary, leaves, right boundary separately.  
   TC: O(n) / SC: O(h)

- **Iterative Approach** — Use stacks/queues to collect boundary nodes in order.  
   TC: O(n) / SC: O(n)

---

### 17 Vertical Order Traversal of a Binary Tree [[987](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/description/)]

- **TreeMap + Nested TreeMap + Priority Queue** — Sort nodes by vertical, then level, then value using nested TreeMaps and PQ.  
   TC: O(n log n) / SC: O(n)

- **BFS + Map with coordinates** — Traverse with BFS, map nodes by coordinates, then sort results.  
   TC: O(n log n) / SC: O(n)

- **DFS + Coordinate Tracking** — Use DFS to track (x,y), then sort collected nodes.  
   TC: O(n log n) / SC: O(n)

---

### 18 Top View of Binary Tree

- **BFS + HashMap** — Traverse level-wise, track first node at each horizontal distance using a HashMap.  
   TC: O(n) / SC: O(n)

- **DFS + HashMap with Level Tracking** — Use DFS with horizontal distance and level, update map only if level is smaller.  
   TC: O(n) / SC: O(n)

- **TreeMap + BFS** — Use TreeMap to keep nodes sorted by horizontal distance during BFS.  
   TC: O(n log n) / SC: O(n)

---

### 19 Bottom View of Binary Tree

- **BFS + Map (horizontal distance → node)** — Use BFS, overwrite map value for each horizontal distance to get bottom-most node.  
   TC: O(n) / SC: O(n)

- **DFS + Map with depth tracking** — DFS traversal with horizontal distance and depth; update map only if deeper node found.  
   TC: O(n) / SC: O(n)

- **Level order traversal + HashMap** — Track nodes by horizontal distance, last encountered node at each distance is bottom view.  
   TC: O(n) / SC: O(n)

---

### 20 Left View of Binary Tree

- **Level Order Traversal (BFS)** — Print first node at each level.  
   TC: O(n) / SC: O(n)

- **Recursive Preorder (DFS)** — Track max level visited and print first node at each level.  
   TC: O(n) / SC: O(h)

---

### 21 Right View of Binary Tree

- **Level Order Traversal (BFS)** — Print last node at each level.  
   TC: O(n) / SC: O(n)

- **Recursive Preorder (DFS)** — Track max level visited, traverse right child first, print first node at each level.  
   TC: O(n) / SC: O(h)

---

### 22 Path Sum II [[113](https://leetcode.com/problems/path-sum-ii/description/)]

- **Recursive DFS + Backtracking** — Explore all paths, backtrack after visiting children.  
   TC: O(n) / SC: O(h)

- **Iterative DFS with Stack** — Stack of `(node, currentPath, sum)` to simulate recursion.  
   TC: O(n) / SC: O(h)

---

### 23 Smallest String Starting From Leaf [[988](https://leetcode.com/problems/smallest-string-starting-from-leaf/description/)]

- **DFS + StringBuilder (prepend at front)** — Use `StringBuilder` to build string from leaf to root by inserting at front.  
   TC: O(n²) / SC: O(h)

- **DFS + ArrayList (compare from end)** — Track path chars in list, build string when at leaf by iterating from end.  
   TC: O(n²) / SC: O(h)

- **DFS + Char Array (optimized)** — Use a char array to track path, backtrack as needed.  
   TC: O(n) avg / SC: O(h)

---

### 24 Longest Univalue Path [[687](https://leetcode.com/problems/longest-univalue-path/description/)]

- **Recursive (Postorder DFS)** — At each node, compute longest univalue path in left & right, extend path if values match.  
   TC: O(n) / SC: O(h)

- **Iterative with Stack (Modified DFS)** — Simulate DFS using stack while tracking parent values. (Less common)  
   TC: O(n) / SC: O(h)

---

### 25 Lowest Common Ancestor of a Binary Tree [[236](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/)]

- **Recursive (Bottom-up)** — Return node if p/q found, else propagate LCA from subtrees.  
   TC: O(n) / SC: O(h)

- **Parent Pointers + HashSet** — Store parent of each node, trace p’s ancestors, check q's path upward.  
   TC: O(n) / SC: O(n)

- **Iterative DFS with Parent Map** — Build parent map using DFS, then backtrack both nodes to find LCA.  
   TC: O(n) / SC: O(n)

---

### 26 Path Sum [[112](https://leetcode.com/problems/path-sum/description/)]

- **Recursive DFS** — Check sum along each root-to-leaf path via recursion.  
   TC: O(n) / SC: O(h)

- **Iterative DFS with Stack** — Use stack to track (node, current sum).  
   TC: O(n) / SC: O(h)

- **Iterative BFS with Queue** — Use queue to track (node, current sum).  
   TC: O(n) / SC: O(h)

---

### 27 Path In Zigzag Labelled Binary Tree [[1104](https://leetcode.com/problems/path-in-zigzag-labelled-binary-tree/description/)]

- **Math + Level Calculation** — Find level using `Math.log2(label)` + 1, compute mirrored label when needed, backtrack to parent.  
   TC: O(log n) / SC: O(1)

- **Recursive Approach** — Recursively compute parent by adjusting mirrored values and collect path.  
   TC: O(log n) / SC: O(log n)

- **Iterative Approach** — Same as math logic but use a loop to build path from target to root.  
   TC: O(log n) / SC: O(log n)

---

### 28 Cycle Length Queries in a Tree [[2586](https://leetcode.com/problems/cycle-length-queries-in-a-tree)]

- **Simulate upward moves to LCA** — Move both nodes up to their LCA by dividing by 2, count steps.  
   TC: O(q * log n) / SC: O(1)

- **Precompute ancestors + LCA queries** — Use binary lifting for faster LCA queries, then calculate path length.  
   TC: O((n + q) * log n) / SC: O(n log n)

---

### 29 Populating Next Right Pointers in Each Node [[116](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/description/)]

- **DFS Pairing Approach** — Recursively connect left-right, right-left, etc.  
   TC: O(n) / SC: O(h)

- **BFS (Level Order using Queue)** — Use queue to connect nodes level by level.  
   TC: O(n) / SC: O(n)

- **Iterative (Using Existing Next Pointers)** — Connect nodes on current level while traversing via `.next` pointers.  
   TC: O(n) / SC: O(1)

---

### 30 Maximum Width of Binary Tree [[662](https://leetcode.com/problems/maximum-width-of-binary-tree/description/)]

- **BFS + Index Tracking** — Use BFS, assign indices to nodes, compute width as `(last - first + 1)` at each level.  
   TC: O(n) / SC: O(n)

- **DFS + Index Map** — Use DFS to track leftmost index at each depth, then compute width.  
   TC: O(n) / SC: O(h)

---

### 31 Check for Children Sum Property in a Binary Tree [[GFG](https://www.geeksforgeeks.org/check-for-children-sum-property-in-a-binary-tree/)]

- **Recursive (Top-down)** — At each node, check `node.data == left.data + right.data`, recurse for children.  
   TC: O(n) / SC: O(h)

- **Iterative (Level Order Traversal)** — Use queue, check sum property at each level iteratively.  
   TC: O(n) / SC: O(n)

---

### 32 All Nodes Distance K in Binary Tree [[863](https://leetcode.com/problems/all-nodes-distance-k-in-binary-tree/description/)]

- **DFS to build Parent Map + BFS from Target** — First map each node’s parent, then BFS from target up to K distance.  
   TC: O(n) / SC: O(n)

- **Pure DFS with Distance Tracking** — Recursively traverse while keeping track of distance from target.  
   TC: O(n) / SC: O(h)

- **DFS to build Graph + BFS** — Convert tree into undirected graph (adjacency list), then BFS from target node.  
   TC: O(n) / SC: O(n)

---

### 33 Amount of Time for Binary Tree to Be Infected [[2385](https://leetcode.com/problems/amount-of-time-for-binary-tree-to-be-infected/description/)]

- **Convert to Graph + BFS** — Convert tree to undirected graph using adjacency list, then run BFS from start node to find max infection time.  
   TC: O(n) / SC: O(n)

- **DFS + Parent Map + Queue** — Track parents while doing DFS, then BFS from start using queue and visited set.  
   TC: O(n) / SC: O(n)

- **DFS (Single Pass with Depth Propagation)** — Recursively calculate max time by simulating infection spread during traversal (more advanced, but doable).  
   TC: O(n) / SC: O(h)

---

### 34 Count Complete Tree Nodes [[222](https://leetcode.com/problems/count-complete-tree-nodes/description/)]

- **Simple Recursive (DFS)** — Recursively count left + right + 1.  
   TC: O(n) / SC: O(h)

- **Optimized Recursive (Height-based)** — Compare left & right subtree heights; if equal, use formula `2^h - 1`.  
   TC: O(log² n) / SC: O(log n)     *IMP*

- **Iterative (Height-based)** — Same logic as optimized recursive, done iteratively.  
   TC: O(log² n) / SC: O(1)

---

### 35 Construct Binary Tree from Preorder and Inorder Traversal [[105](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/)]

- **Recursive with HashMap** — Use preorder to pick root, find root in inorder using a hashmap for O(1) lookup, recursively build left/right subtrees.  
   TC: O(n) / SC: O(n)

- **Recursive without HashMap** — Same as above but search root index in inorder with linear scan each time.  
   TC: O(n²) / SC: O(n)

- **Iterative Approach** — Use stack to simulate recursion based on preorder and inorder arrays.  
   TC: O(n) / SC: O(n)

---

### 36 Flatten Binary Tree to Linked List [[114](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/description/)]

- **Recursive (Reverse Postorder)** — Process right, left, then root recursively, track previous node.  
   TC: O(n) / SC: O(h)

- **Iterative with Stack** — Use stack to mimic reverse preorder traversal, adjust pointers on the fly.  
   TC: O(n) / SC: O(n)

- **Morris Traversal (Threaded Binary Tree)** — O(1) space by rewiring left subtrees to predecessors.  
   TC: O(n) / SC: O(1)

---

### 37 Most Frequent Subtree Sum [[508](https://leetcode.com/problems/most-frequent-subtree-sum/description/)]

- **Postorder DFS + HashMap** — Postorder compute subtree sums, track frequencies in a map.  
   TC: O(n) / SC: O(n)

- **Postorder DFS + Counter Array** — Similar to above but with a pre-sized array if sum ranges are known (rare case).  
   TC: O(n) / SC: O(n)

---
