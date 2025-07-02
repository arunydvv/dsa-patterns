
# 📖 Minimum Time to Complete Trips (LeetCode 2187)

**Problem Link:** [https://leetcode.com/problems/minimum-time-to-complete-trips/](https://leetcode.com/problems/minimum-time-to-complete-trips/)

----------

## 📜 Problem Statement:

You’re given:

-   An array `time` where `time[i]` is the time one bus takes to complete a single trip.
    
-   An integer `totalTrips`.
    

You need to find the **minimum total time** such that all buses together can complete at least `totalTrips`.



## 📊 Approaches (In Increasing Order of Optimisation)


### 1️⃣ Brute-Force Linear Time Simulation (TLE)

**Idea:**

-   Start from `t = 1`, for each time unit incrementally, count how many trips have been completed by all buses.
    
-   Stop when total trips ≥ `totalTrips`.
    

**Time Complexity:** `O(max_time * totalTrips * n)`  
**Space Complexity:** `O(1)`

✅ Impractical for large inputs.

----------

### 2️⃣ Parametric Binary Search (Optimal)

**Idea:**

-   Use **binary search on answer space** (time) from `1` to `max(time) * totalTrips`.
    
-   For a given time `mid`, check how many trips total buses can complete.
    
-   If ≥ `totalTrips`, try to minimize time further by moving `end = mid - 1`.
    
-   Else, move `start = mid + 1`.
    

**Time Complexity:** `O(n log(max_time × totalTrips))`  
**Space Complexity:** `O(1)`

✅ Clean and optimal.



## 📦 Code (Approach-wise)



### 1️⃣ Brute-Force Linear Time Simulation (Concept Only — TLE)

```java
public long minimumTimeBrute(int[] time, int totalTrips) {
    long currentTime = 0;
    while (true) {
        long count = 0;
        for (int t : time) {
            count += currentTime / t;
        }
        if (count >= totalTrips) return currentTime;
        currentTime++;
    }
}

```

----------

### 2️⃣ Binary Search + Feasibility Check (Optimal)

```java
public long minimumTime(int[] time, int totalTrips) {
    long start = 1;
    long end = (long) Arrays.stream(time).max().getAsInt() * totalTrips;

    while (start <= end) {
        long mid = start + (end - start) / 2;
        if (isPossible(totalTrips, time, mid)) {
            end = mid - 1;
        } else {
            start = mid + 1;
        }
    }
    return start;
}

boolean isPossible(int totalTrips, int[] time, long currentTime) {
    long count = 0;
    for (int t : time) {
        count += currentTime / t;
        if (count >= totalTrips) return true;
    }
    return false;
}

```



## ✅ Final Summary:

Approach

Time Complexity

Space Complexity

**Brute-Force Linear Simulation (TLE)**

`O(max_time * totalTrips * n)`

`O(1)`

**Binary Search + Feasibility (Optimal)**

`O(n log(max_time × totalTrips))`

`O(1)`

----------

## 🔍 Any Sliding Window or Heap Based Approach?

**No.**  
This problem is a classic example of **parametric search (binary search on answer)** because:

-   You're searching over a monotonic space of possible answers (time).
    
-   No continuous subarray/subsequence needs to be found.
    
-   Sliding window / heap approaches are not applicable.
    

