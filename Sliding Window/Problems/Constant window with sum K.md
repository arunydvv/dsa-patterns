
# ✅ Subarrays with Sum K [[560](https://leetcode.com/problems/subarray-sum-equals-k/)]

## Problem  
Given an array of integers `nums` and an integer `k`, return the total number of continuous subarrays whose sum equals to `k`.

---

## 📌 Approaches  

| Approach                     | Time Complexity | Space Complexity |
|:----------------------------|:----------------|:----------------|
| **Constant Window Sliding Window (Positive numbers only)** | O(n) | O(1) |
| **Prefix Sum + HashMap (Optimized for any numbers)** | O(n) | O(n) |

---

## ✅ Approach 1: Constant Window Sliding Window  

### Intuition  
Use a two-pointer window `[left, right]` and expand the window by moving `right`.  
If the sum exceeds `k`, shrink from the left.  
Increment count when sum matches `k`.  

### Constraints  
✅ Only works with **positive numbers**.  
❌ Not usable if negative numbers are in the array.

### Code  

```java
class Solution {
    public int countSubarraysWithSumK(int[] nums, int k) {
        int count = 0, windowSum = 0, left = 0;
        for (int right = 0; right < nums.length; right++) {
            windowSum += nums[right];
            while (windowSum > k && left <= right) {
                windowSum -= nums[left];
                left++;
            }
            if (windowSum == k) count++;
        }
        return count;
    }
}

```

----------

## ✅ Approach 2: Prefix Sum + HashMap (Optimized)

### Intuition

Track prefix sums as you iterate, storing their frequencies in a HashMap.  
At each step, check if `currentSum - k` exists — it indicates a subarray summing to `k`.

### Constraints

✅ Works for **any integers** — positive, negative, or zero.

### Code

```java
class Solution {
    public int countSubarraysWithSumK(int[] nums, int k) {
        Map<Integer, Integer> prefixSumCount = new HashMap<>();
        prefixSumCount.put(0, 1);  // base case

        int prefixSum = 0, count = 0;
        for (int num : nums) {
            prefixSum += num;

            if (prefixSumCount.containsKey(prefixSum - k)) {
                count += prefixSumCount.get(prefixSum - k);
            }

            prefixSumCount.put(prefixSum, prefixSumCount.getOrDefault(prefixSum, 0) + 1);
        }

        return count;
    }
}

```

----------

## 📌 Key Notes

-   **Constant Window Sliding Window**: Linear time, constant space — but limited to positive numbers.
    
-   **Prefix Sum + HashMap**: Linear time and space — works for both positive and negative values.
    

----------

## 📚 Related LeetCode Problems

Problem

Approach

[560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)

Prefix Sum

[209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)

Sliding Window

[485. Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/)

Sliding Window

[1004. Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)

Sliding Window

[1343. Number of Sub-arrays of Size K and Average ≥ Threshold](https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold/)

Sliding Window

[1456. Maximum Number of Vowels in a Substring of Given Length](https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/)

Sliding Window

[1248. Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/)

Prefix Sum

----------

## 📌 When to Use

-   **Constant Window**: Sum, max, min, or count in a continuous subarray with **positive numbers only**.
    
-   **Prefix Sum + HashMap**: Whenever input may have **negative numbers** or if subarray sum problems need flexibility.
    

----------

## ✅ Summary

-   **Constant Window Sliding Window **
Positive only   TC O(n) SC O(1)    Fast, simple

- Prefix Sum + HashMap
	Any numbers O(n)  O(n)  Robust
