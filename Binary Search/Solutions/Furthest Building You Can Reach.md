# 📌 Furthest Building You Can Reach

**Problem Link:** [LeetCode 1642](https://leetcode.com/problems/furthest-building-you-can-reach/)


## 📖 Problem Statement

You are given:
- An integer array `heights` representing the height of buildings in a row.
- `bricks` and `ladders` representing resources to climb buildings.

You start at building `0` and move to building `i + 1`:
- If `heights[i+1] <= heights[i]` → no resources needed.
- If `heights[i+1] > heights[i]` → climb difference using either:
  - **Bricks** equal to the height difference.
  - **One ladder**.

**Goal:**  
Return the **furthest building index** you can reach before running out of resources.



## 📌 Approach

### ✅ Idea:
- Use **binary search on the possible answer (index)** from `0` to `heights.length-1`.
- For each candidate index:
  - Simulate climbing using a **min-heap (priority queue)**.
  - Always use bricks for the smallest climbs and save ladders for bigger ones.

### ✅ Why Binary Search?
- The problem asks for the *maximum reachable index under constraints*, which can be efficiently found via **binary search on the index space** with a helper function that checks if reaching a given index is possible.

---

## 📊 Time and Space Complexity

| Operation                    | Time Complexity         | Space Complexity |
|:----------------------------|:------------------------|:----------------|
| Binary Search on index space | O(log n)                  | O(1)             |
| Simulating climbs at each mid| O(n log n) (because of PQ)| O(n)             |
| **Total**                    | O(n log n \* log n)       | O(n)             |

---

## 📦 Companies Asked In:

- **Amazon**
- **Google**
- **Microsoft**
- **Uber**
- **Facebook (Meta)**

Very popular for testing **binary search on answers + greedy resource allocation using heaps**.

---

## 📌 Code (Java)

```java
class Solution {
    public int furthestBuilding(int[] heights, int bricks, int ladders) {
        int start = 0;
        int end = heights.length - 1;
        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (canReach(heights, bricks, ladders, mid)) {
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }
        return end;
    }

    boolean canReach(int[] heights, int bricks, int ladders, int target) {
        if (target == 0) return true;
        PriorityQueue<Integer> pq = new PriorityQueue<>();
        for (int i = 1; i <= target; i++) {
            int diff = heights[i] - heights[i - 1];
            if (diff > 0) pq.add(diff);
        }

        while (!pq.isEmpty()) {
            int climb = pq.poll();
            if (bricks >= climb) bricks -= climb;
            else if (ladders > 0) ladders--;
            else return false;
        }
        return true;
    }
}

```

----------

## 📚 Notes

-   **Use bricks for the smallest jumps first** — handled via a min-heap.
    
-   **Use ladders for largest jumps** when bricks are insufficient.
    
-   Cleverly combining **binary search on answer** and **priority queue** for resource management.
    
-   Clean use-case of the **binary search + greedy + heap optimization pattern**.
    

----------

## 📌 Similar Problems / Patterns

-   **Minimum Number of Refueling Stops**
    
-   **K-th Smallest Element in a Sorted Matrix**
    
-   **Path with Minimum Effort**
    
-   Binary Search on Answer problems
    
-   Greedy problems using PriorityQueue (Min Heap / Max Heap)
    

----------

## ✅ Summary

Efficient O(n log n log n) solution combining:

-   **Binary Search on possible furthest index**
    
-   **PriorityQueue for greedy resource allocation**
    
-   Neat edge-case handling for zero jumps
    

A great interview problem testing both algorithmic patterns and optimization awareness.

