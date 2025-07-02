

## 📖 Maximum Value at a Given Index in a Bounded Array (LeetCode 1802)



## 📜 Problem Statement:

Given three integers:

-   `n` (length of array),
    
-   `index` (target position),
    
-   `maxSum` (maximum total sum of the array)
    

Find the maximum possible value at position `index` such that:

-   All array elements are **positive integers**
    
-   Difference between adjacent elements is at most **1**
    
-   The total sum ≤ `maxSum`
    

----------

## 📊 Approaches (Increasing Order of Optimisation)

----------

### 1️⃣ Brute-Force Incremental Check (TLE)

**Idea:**

-   Start from 1 at `index`, increase its value one by one.
    
-   At each step, fill other positions according to adjacent difference constraint.
    
-   Check if total sum exceeds `maxSum`.
    
-   If it does — stop.
    

**Time Complexity:** `O(maxSum)`  
**Space Complexity:** `O(1)`

✅ Not practical for constraints up to 10⁹

----------

### 2️⃣ Binary Search + Feasibility Check (Optimal)

**Idea:**

-   Use binary search to find maximum possible value at `index`.
    
-   For each mid value, check whether it's possible to build an array of size `n` obeying adjacent differences ≤ 1 and total sum ≤ `maxSum`.
    
-   If feasible, move to higher values; otherwise, lower.
    

**Time Complexity:** `O(log(maxSum) * log n)`  
**Space Complexity:** `O(1)`

✅ Best possible solution for constraints

----------

## 📦 Code (Approach-wise)

### 1️⃣ Brute-Force Incremental Check (TLE)

_(Conceptual only — impractical to code for n, maxSum ≤ 10⁹)_


### 2️⃣ Binary Search + Feasibility Check (Optimal)

```java
class Solution {
    public int maxValue(int n, int index, int maxSum) {
        int left = 1, right = maxSum, ans = 0;
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (isPossible(n, index, mid, maxSum)) {
                ans = mid;
                left = mid + 1;
            } else right = mid - 1;
        }
        return ans;
    }

    boolean isPossible(int n, int index, int value, int maxSum) {
        long sum = value;
        sum += sumSide(value - 1, index);            // left side sum
        sum += sumSide(value - 1, n - index - 1);    // right side sum
        return sum <= maxSum;
    }

    long sumSide(int peak, int count) {
        if (count <= peak) {
            long high = peak;
            long low = peak - count + 1;
            return (high + low) * count / 2;
        } else {
            long sum = (long)(peak + 1) * peak / 2;
            sum += (count - peak);
            return sum;
        }
    }
}

```


## ✅ Final Summary

**Brute-Force Incremental (TLE)**

`Time Complexity O(maxSum)`

`Space Complexity O(1)`

**Binary Search + Feasibility**

`Time Complexity O(log(maxSum) * log n)`

`Space Complexity O(1)`

