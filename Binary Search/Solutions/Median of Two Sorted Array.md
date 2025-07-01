## ✅ Median of Two Sorted Arrays — LeetCode [Problem #4](https://leetcode.com/problems/median-of-two-sorted-arrays/)



### 📖 Problem Statement:

Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return the median of the two sorted arrays.  
The overall run time complexity should be **O(log(min(m,n)))**.

----------

### 📜 Code (Java — Binary Search on Partition)

```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        int n1 = nums1.length;
        int n2 = nums2.length;

        if (n1 > n2) return findMedianSortedArrays(nums2, nums1);  // binary search on smaller array

        int total = n1 + n2;
        int half = (total + 1) / 2;
        int start = 0;
        int end = n1;

        while (start <= end) {
            int mid1 = (start + end) / 2;
            int mid2 = half - mid1;

            int afirst = (mid1 > 0) ? nums1[mid1 - 1] : Integer.MIN_VALUE;
            int bfirst = (mid2 > 0) ? nums2[mid2 - 1] : Integer.MIN_VALUE;
            int alast  = (mid1 < n1) ? nums1[mid1] : Integer.MAX_VALUE;
            int blast  = (mid2 < n2) ? nums2[mid2] : Integer.MAX_VALUE;

            if (afirst <= blast && bfirst <= alast) {
                if (total % 2 == 0) {
                    return ((double) Math.max(afirst, bfirst) + Math.min(alast, blast)) / 2;
                } else {
                    return (double) Math.max(afirst, bfirst);
                }
            } else if (afirst > blast) {
                end = mid1 - 1;
            } else {
                start = mid1 + 1;
            }
        }
        return 0;  // should never reach here if inputs are valid
    }
}

```

----------

## 📊 Time & Space Complexity

Approach  --> Binary Search Partition Method

Time Complexity  `O(log(min(m, n)))`

Space Complexity `O(1)`

## ⚠️ Important Edge Cases & Precautions

1.  **One or both arrays empty**
    
    -   If one array is empty, it should correctly compute median from the other array.
        
2.  **Arrays with unequal sizes**
    
    -   Always binary search on the **smaller array** for optimal time complexity and to prevent index out of bound errors.
        
3.  **Even vs Odd Total Length**
    
    -   Different logic for when total length is even (average of two middle values) vs odd (middle value only)
        
4.  **Handling integer limits**
    
    -   Use `Integer.MIN_VALUE` and `Integer.MAX_VALUE` to handle empty partitions on either side without special conditions.
        
5.  **Arrays with duplicate elements**
    
    -   Should handle duplicates naturally due to comparison logic.
        
6.  **Very large arrays**
    
    -   No actual merging — binary search ensures logarithmic time on the smaller array.
        
7.  **Identical arrays**
    
    -   Should compute median correctly even if both arrays have exactly the same elements.
        





## 📌 Intuition / Explanation

-   Use **binary search on the smaller array**.
    
-   Partition both arrays so left side contains `half` elements.
    
-   Compare maximum of left partitions and minimum of right partitions.
    
-   If correct partition found:
    
    -   If total elements are even, median is average of max(left parts) and min(right parts)
        
    -   If odd, median is max(left parts)
        
-   Otherwise, adjust binary search range.
    

----------

