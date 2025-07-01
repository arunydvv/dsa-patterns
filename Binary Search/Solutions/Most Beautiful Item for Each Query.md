
# 📌 Maximum Beauty of an Item After Price Query

**Problem Link:** [LeetCode 2070](https://leetcode.com/problems/maximum-beauty-of-an-item-after-price-query/)

---

## 📖 Problem Statement

You are given:
- An array `items`, where each `items[i] = [price, beauty]`
- An array `queries` where each `queries[i]` is a price limit

For each query, find the **maximum beauty of any item whose price is less than or equal to the query price**.

---

## 📌 Approach

1. **Sort the items by price** — so we can binary search over price thresholds.
2. **Build a prefix maximum beauty array** — so for any index, we can get the maximum beauty of all items up to that price.
3. **For each query:**
   - Use **binary search (upper bound)** to find the index of the first item with price **greater than** the query price.
   - The maximum beauty is then the prefix value at `index - 1`.
   - If no item exists for a query (index == 0), answer is 0.

---

## 📊 Time and Space Complexity

| Operation             | Time Complexity | Space Complexity |
|:---------------------|:----------------|:----------------|
| Sorting items         | O(n log n)       | O(1)             |
| Building prefix array | O(n)             | O(n)             |
| Answering queries     | O(m log n)       | O(m)             |
| **Total**             | O((n + m) log n) | O(n + m)         |

Where `n` = number of items, `m` = number of queries.

---

## 📦 Companies Asked In:

- **Amazon**
- **Google**
- **Microsoft**
- **Adobe**
- **Flipkart**
- **ByteDance (TikTok)**
- **Snapdeal**

This problem is commonly asked in interviews focusing on **binary search on sorted arrays + prefix maximums pattern**.

---

## 📌 Code (Java)

```java
class Solution {
    public int[] maximumBeauty(int[][] items, int[] queries) {
        // Sort items by price
        Arrays.sort(items, (a, b) -> a[0] - b[0]);

        // Build prefix max beauty array
        int n = items.length;
        int[] prefix = new int[n];
        prefix[0] = items[0][1];
        for (int i = 1; i < n; i++) {
            prefix[i] = Math.max(prefix[i - 1], items[i][1]);
        }

        // Process each query
        int[] ans = new int[queries.length];
        for (int i = 0; i < queries.length; i++) {
            int index = upperBound(items, queries[i]) - 1;
            ans[i] = (index >= 0) ? prefix[index] : 0;
        }
        return ans;
    }

    // Returns index of first element with price > target
    int upperBound(int[][] arr, int target) {
        int low = 0, high = arr.length - 1;
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (arr[mid][0] <= target)
                low = mid + 1;
            else
                high = mid - 1;
        }
        return low;
    }
}
```

## 📚 Notes

-   Classic use-case of **prefix maximums** combined with **binary search**.
    
-   Be careful with **upper bound binary search implementation**:
    
    -   Return `low` for index of first element > target.
        
    -   Subtract 1 to get last element ≤ target.
        
-   Important optimization: **Sorting once** and answering multiple queries efficiently.
    



## 📌 Similar Patterns

-   Binary Search over Sorted Array
    
-   Prefix Max Arrays
    
-   Range Query Optimization
    
-   Custom Binary Search Variants