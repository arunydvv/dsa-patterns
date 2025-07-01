
## 📄 Kth Element of Two Sorted Arrays

**Problem:**  
Given two sorted arrays `nums1` and `nums2` and an integer `k`, find the **kth smallest element** in their merged sorted order **without actually merging** them.

**Constraint:**  
Time Complexity: **O(log(min(n, m)))**

----------

## 📜 Code (Java — Binary Search on Partition)

```java
class Solution {
    public int kthElement(int[] nums1, int[] nums2, int k) {
        int n1 = nums1.length, n2 = nums2.length;
        if (n1 > n2) return kthElement(nums2, nums1, k);

        if (n1 + n2 < k) return -1;
        int start = Math.max(0, k - n2), end = Math.min(k, n1);

        while (start <= end) {
            int mid1 = (start + end) / 2;
            int mid2 = k - mid1;

            int afirst = (mid1 > 0) ? nums1[mid1 - 1] : Integer.MIN_VALUE;
            int bfirst = (mid2 > 0) ? nums2[mid2 - 1] : Integer.MIN_VALUE;
            int alast  = (mid1 < n1) ? nums1[mid1] : Integer.MAX_VALUE;
            int blast  = (mid2 < n2) ? nums2[mid2] : Integer.MAX_VALUE;

            if (afirst <= blast && bfirst <= alast)
                return Math.max(afirst, bfirst);
            else if (afirst > blast)
                end = mid1 - 1;
            else
                start = mid1 + 1;
        }
        return -1;
    }
}

```



## 📊 Complexity

Time Complexity  **O(log(min(n, m)))**

Space Complexity **O(1)**



## 📌 Key Points (Short)

-   ✅ **Binary Search on smaller array**
    
-   ✅ **Partition arrays so left parts have `k` elements**
    
-   ✅ **Use Integer.MIN_VALUE and MAX_VALUE for out-of-bound handling**
    
-   ✅ **Find max of left parts as kth element**
    
-   ✅ **Start = max(0, k - n2), End = min(k, n1)** to avoid invalid partitions
    

----------

## 📦 Edge Cases

-   If **k > n1 + n2** → return `-1`
    
-   If **one array empty**, should still work
    
-   Arrays can have **duplicates** and unequal sizes
    

----------

## 📌 Why this `start` and `end`?

We set:
`start = max(0, k - n2)`
`end   = min(k, n1)`

**Reason:**

-   `mid1` (elements taken from `nums1`) must be **at least 0** and **at most n1**
    
-   `mid2 = k - mid1` (elements taken from `nums2`) must be **between 0 and n2**
    

To avoid `mid2` being negative or exceeding `n2`,

-   Minimum value of `mid1` is `k - n2` (if nums2 can't fully contribute k elements)
    
-   Maximum value of `mid1` is `min(k, n1)` (if nums1 doesn’t have enough elements)
    

This keeps both partitions valid.

----------

## ✅ Example

```text
nums1 = [2, 3, 6, 7, 9]
nums2 = [1, 4, 8, 10]
k = 5

Output: 6

```

