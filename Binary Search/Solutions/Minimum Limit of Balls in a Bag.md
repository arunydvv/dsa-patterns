

## 📖 Minimum Limit of Balls in a Bag (LeetCode 1760)

**Problem Link:** [https://leetcode.com/problems/minimum-limit-of-balls-in-a-bag/](https://leetcode.com/problems/minimum-limit-of-balls-in-a-bag/)

----------

## 📜 Problem Statement:

You're given an array `nums` where `nums[i]` is the number of balls in the `iᵗʰ` bag. You can perform a number of operations where in each operation you split a bag of balls into two bags with positive number of balls.

You’re also given an integer `maxOperations`.  
Return the **minimum possible value of the maximum number of balls in any bag after performing at most `maxOperations` operations**.

----------

## 📊 Approaches (In Increasing Order of Optimisation)

----------

### 1️⃣ Brute-Force Linear Scan (TLE)

**Idea:**

-   Start from `maxValue = 1`.
    
-   For each possible `maxValue`, check how many operations are required to ensure all bags have `≤ maxValue`.
    
-   If operations exceed `maxOperations`, increase `maxValue`.
    
-   Repeat until finding a valid one.
    

**Time Complexity:** `O(n * max(nums))`  
**Space Complexity:** `O(1)`

✅ Not practical for large constraints.

----------

### 2️⃣ Binary Search + Feasibility Check (Optimal)

**Idea:**

-   Use **parametric search (binary search on answer)** to find the minimum possible `maxValue`.
    
-   For each `mid` value during binary search, check how many operations would be needed to reduce all bags to `≤ mid`.
    
-   If total operations needed is within `maxOperations`, try a smaller `mid`; else, increase it.
    

**Time Complexity:** `O(n log max(nums))`  
**Space Complexity:** `O(1)`

✅ Fastest and cleanest solution.

----------

## 📦 Code (Approach-wise)

----------

### 1️⃣ Brute-Force Linear Scan (TLE)

```java
public int minimumSizeBrute(int[] nums, int maxOperations) {
    int maxVal = Arrays.stream(nums).max().getAsInt();
    for (int limit = 1; limit <= maxVal; limit++) {
        int ops = 0;
        for (int num : nums) {
            if (num > limit) ops += (num - 1) / limit;
        }
        if (ops <= maxOperations) return limit;
    }
    return -1;
}

```

----------

### 2️⃣ Binary Search + Feasibility Check (Optimal)

```java
public int minimumSize(int[] nums, int maxOperations) {
    int left = 1, right = Arrays.stream(nums).max().getAsInt();
    while (left < right) {
        int mid = left + (right - left) / 2;
        if (isPossible(nums, maxOperations, mid)) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    return left;
}

boolean isPossible(int[] nums, int maxOperations, int maxSize) {
    int ops = 0;
    for (int num : nums) {
        ops += (num - 1) / maxSize;
        if (ops > maxOperations) return false;
    }
    return true;
}

```

----------

## ✅ Final Summary:

Approach

Time Complexity

Space Complexity

**Brute-Force Linear Scan (TLE)**

`O(n * max(nums))`

`O(1)`

**Binary Search + Feasibility**

`O(n log max(nums))`

`O(1)`

----------

## 📌 Notes:

-   Sliding window isn’t applicable — problem isn’t about subarrays or continuous ranges.
    
-   Heap-based approaches not helpful — problem revolves around **global max value limiting via splitting**.
    
-   Greedy won’t work directly as total operation count depends on all bag sizes together.
    

----------
