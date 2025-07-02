

## 📖 Furthest Building You Can Reach (LeetCode 1642)

**Problem Link:** [https://leetcode.com/problems/furthest-building-you-can-reach/](https://leetcode.com/problems/furthest-building-you-can-reach/)



## 📜 Problem Summary

You're given an array `heights`, and a number of `bricks` and `ladders`. When moving from building `i` to `i+1`:

-   If `heights[i+1] > heights[i]`, you must climb the difference.
    
-   You can use either:
    
    -   That many `bricks`
        
    -   One `ladder`
        
-   Find the furthest building you can reach.
    

----------

## 📊 Approaches (In Increasing Order of Optimisation)



### 1️⃣ DP with Memoization (TLE)

**Idea:**  
Use recursion with memoization, storing (index, bricks, ladders) as the state.

**Time Complexity:** `O(n * bricks * ladders)`  
**Space Complexity:** `O(n * bricks * ladders)`

```java
public int furthestBuildingDP(int[] heights, int bricks, int ladders) {
    Map<String, Integer> memo = new HashMap<>();
    return dp(heights, 0, bricks, ladders, memo);
}

private int dp(int[] heights, int i, int bricks, int ladders, Map<String, Integer> memo) {
    if (i == heights.length - 1) return i;
    String key = i + "," + bricks + "," + ladders;
    if (memo.containsKey(key)) return memo.get(key);

    int diff = heights[i + 1] - heights[i];
    int furthest = i;
    if (diff <= 0) furthest = dp(heights, i + 1, bricks, ladders, memo);
    else {
        if (bricks >= diff)
            furthest = Math.max(furthest, dp(heights, i + 1, bricks - diff, ladders, memo));
        if (ladders > 0)
            furthest = Math.max(furthest, dp(heights, i + 1, bricks, ladders - 1, memo));
    }

    memo.put(key, furthest);
    return furthest;
}

```

----------

### 2️⃣ Greedy Without Heap (Inefficient)

**Idea:**  
Use bricks first when possible, then ladders.

**Time Complexity:** `O(n²)`  
**Space Complexity:** `O(1)`

```java
public int furthestBuildingNaiveGreedy(int[] heights, int bricks, int ladders) {
    for (int i = 0; i < heights.length - 1; i++) {
        int diff = heights[i + 1] - heights[i];
        if (diff <= 0) continue;

        if (bricks >= diff) bricks -= diff;
        else if (ladders > 0) ladders--;
        else return i;
    }
    return heights.length - 1;
}

```

----------

### 3️⃣ Max-Heap on Bricks Used (Greedy Variant)

**Idea:**  
Use a max-heap to track climbs and swap the largest climbs for ladders when needed.

**Time Complexity:** `O(n log n)`  
**Space Complexity:** `O(n)`

```java
public int furthestBuildingMaxHeap(int[] heights, int bricks, int ladders) {
    PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());

    for (int i = 0; i < heights.length - 1; i++) {
        int diff = heights[i + 1] - heights[i];
        if (diff <= 0) continue;

        bricks -= diff;
        maxHeap.add(diff);

        if (bricks < 0) {
            if (ladders > 0) {
                bricks += maxHeap.poll();
                ladders--;
            } else return i;
        }
    }
    return heights.length - 1;
}

```

----------

### 4️⃣ Min-Heap (Optimal Greedy)

**Idea:**  
Use a min-heap to always assign ladders to the largest climbs.

**Time Complexity:** `O(n log n)`  
**Space Complexity:** `O(n)`

```java
public int furthestBuildingMinHeap(int[] heights, int bricks, int ladders) {
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();

    for (int i = 0; i < heights.length - 1; i++) {
        int diff = heights[i + 1] - heights[i];
        if (diff <= 0) continue;

        minHeap.add(diff);
        if (minHeap.size() > ladders) {
            bricks -= minHeap.poll();
        }
        if (bricks < 0) return i;
    }
    return heights.length - 1;
}

```

----------

### 5️⃣ Binary Search + Feasibility Check (Parametric Search)

**Idea:**  
Binary search on the furthest reachable index and for each mid-point check feasibility using the min-heap method.

**Time Complexity:** `O(n log n log n)`  
**Space Complexity:** `O(n)`

```java
public int furthestBuildingBinarySearch(int[] heights, int bricks, int ladders) {
    int left = 0, right = heights.length - 1, ans = 0;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (canReach(heights, bricks, ladders, mid)) {
            ans = mid;
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return ans;
}

private boolean canReach(int[] heights, int bricks, int ladders, int pos) {
    PriorityQueue<Integer> minHeap = new PriorityQueue<>();
    for (int i = 0; i < pos; i++) {
        int diff = heights[i + 1] - heights[i];
        if (diff <= 0) continue;
        minHeap.add(diff);
        if (minHeap.size() > ladders) bricks -= minHeap.poll();
        if (bricks < 0) return false;
    }
    return true;
}

```

----------

