
# 📊 Binary Search on Answer: Find Minimum Feasible Value

## ✅ Problem Description

Given an array of positive integers `nums` and an integer `limit`, find the minimum value `x` such that performing an operation on each element of the array using `x` satisfies a certain constraint (like total operations/time within `limit`).

This is a **Binary Search on Answer** problem — where we search in the possible range of answers rather than positions.

---

## ✅ Approach

### Binary Search on Answer:
- Set the initial search range: `low = 1`, `high = max value in nums`
- While `low < high`
  - Find `mid`
  - If `requiredUnits(nums, mid)` exceeds `limit`
    - Move `low` to `mid + 1`
  - Else, move `high` to `mid`
- Return `low` as the minimum feasible value.

**Time Complexity:** O(n log m)  
**Space Complexity:** O(1)

---

## ✅ Code

```java
class Solution {
    public int findMinimumValue(int[] nums, int limit) {
        int maxValue = Integer.MIN_VALUE;
        for (int num : nums) {
            if (num > maxValue) maxValue = num;
        }

        int low = 1;
        int high = maxValue;

        while (low < high) {
            int mid = low + (high - low) / 2;
            if (requiredUnits(nums, mid) > limit) {
                low = mid + 1;
            } else {
                high = mid;
            }
        }

        return low;
    }

    int requiredUnits(int[] nums, int value) {
        int total = 0;
        for (int num : nums) {
            total += (num - 1) / value + 1;
        }
        return total;
    }
}

```

----------

## ✅ Similar Problems (Binary Search on Answer)


**Koko Eating Bananas**	[LeetCode 875](https://leetcode.com/problems/koko-eating-bananas/)

**Smallest Divisor Given a Threshold**	[LeetCode 1283](https://leetcode.com/problems/smallest-divisor-given-a-threshold/)

**Minimized Maximum of Products Distributed to Any Store**[LeetCode 2064](https://leetcode.com/problems/minimized-maximum-of-products-distributed-to-any-store/)

**Minimum Time to Repair Cars**	[LeetCode 2594](https://leetcode.com/problems/minimum-time-to-repair-cars/)

**Capacity to Ship Packages Within D Days**	[LeetCode 1011](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/)

**Split Array Largest Sum**	[LeetCode 410](https://leetcode.com/problems/split-array-largest-sum/)

**Minimum Number of Days to Make m Bouquets**	[LeetCode 1482](https://leetcode.com/problems/minimum-number-of-days-to-make-m-bouquets/)

**Minimum Speed to Arrive on Time**	[LeetCode 1870](https://leetcode.com/problems/minimum-speed-to-arrive-on-time/)

----------

## ✅ Pattern Summary

-   **Binary Search on Answer Space**
    
-   When the search space is over a range of numerical answers (like speeds, days, divisors, capacities) and a helper function determines feasibility.


## ✅ Tags

`Binary Search on Answer` `Greedy` `Simulation`



## ✅ Notes

-   Avoid `low = 0` when dividing — as it can lead to division by zero errors.
    
-   Always use `mid = low + (high - low) / 2` to avoid integer overflow.
    
