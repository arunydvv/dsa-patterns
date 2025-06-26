

# 📌 Longest Subarray with Sum ≤ K

----------

## 📖 Problem

Given an array of integers `arr` and an integer `K`, find the **length of the longest contiguous subarray** whose sum is **less than or equal to K**.

----------

## 📌 Idea

We want to track a subarray sum and dynamically adjust the window size to maximize the subarray length while ensuring its sum does not exceed `K`.

We’ll explore both:

-   **Brute Force**
    
-   **Sliding Window (Optimized)**  
    **Note:** Sliding Window works efficiently when all elements are **positive**.
    

----------

## 📌 Approaches

### 🔸 Approach 1: Brute Force

-   Use two nested loops.
    
-   For each starting index, check the sum of all possible subarrays starting from it.
    
-   Track maximum length where sum ≤ K.
    

#### ✅ Code

```java
public int longestSubarrayBruteForce(int[] arr, int k) {
    int n = arr.length;
    int maxLen = 0;

    for (int i = 0; i < n; i++) {
        int sum = 0;
        for (int j = i; j < n; j++) {
            sum += arr[j];
            if (sum <= k) {
                maxLen = Math.max(maxLen, j - i + 1);
            }
        }
    }
    return maxLen;
}

```

#### 📊 Time Complexity: O(N²)

#### 📦 Space Complexity: O(1)

----------

### 🔸 Approach 2: Sliding Window (For **Positive Integers Only**)

-   Use two pointers `left` and `right`.
    
-   Expand `right` and add elements to `windowSum`.
    
-   When `windowSum > K`, shrink window from the left.
    
-   Track the maximum window length where sum ≤ K.
    

#### ✅ Code

```java
public int longestSubarraySlidingWindow(int[] arr, int k) {
    int n = arr.length;
    int left = 0, right = 0, windowSum = 0, maxLen = 0;

    while (right < n) {
        windowSum += arr[right];

        while (windowSum > k) {
            windowSum -= arr[left];
            left++;
        }

        maxLen = Math.max(maxLen, right - left + 1);
        right++;
    }
    return maxLen;
}

```

#### 📊 Time Complexity: O(N)

#### 📦 Space Complexity: O(1)

----------

## 📌 When to Use This Pattern

-   When you need to find **maximum or minimum length subarrays** under a specific sum or product constraint.
    
-   Works efficiently with **positive-only arrays**.
    
-   Suitable for **real-time adjustment problems** where you need to expand and contract a window based on some condition.
    

----------

## 📌 Important Cases

-   All elements are **positive** → Sliding Window works.
    
-   If elements are **mixed (positive and negative)** → Sliding Window breaks, must use prefix sum + map, or other techniques.
    

----------

## 📌 Edge Cases

Case

Expected Handling

Empty Array

Return 0

All elements > K

Return 0

K = 0

Return 0

All subarrays sum ≤ K

Return n

Single element ≤ K

Return 1

----------

## 📌 Related LeetCode Problems

Problem

Link

Maximum Size Subarray Sum Equals k

[LeetCode 325](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/)

Subarray Sum Equals k

[LeetCode 560](https://leetcode.com/problems/subarray-sum-equals-k/)

Longest Subarray of 1's After Deleting One Element

[LeetCode 1493](https://leetcode.com/problems/longest-subarray-of-1s-after-deleting-one-element/)

----------

## 📌 Summary

Approach

Time Complexity

Space Complexity

Applicable When

Brute Force

O(N²)

O(1)

Always

Sliding Window

O(N)

O(1)

When all elements are positive

----------

## ✅ Note

If **negative numbers** are present — use **Prefix Sum + HashMap** or **Modified Sliding Window with careful handling**.

----------
