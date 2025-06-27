# 📚 Lower Bound and Upper Bound in a Sorted Array using Binary Search 


## ✅ Lower Bound:

> The **lower bound of a target** is the index of the first element greater than or equal to the target.

```java
// Returns the index of the lower bound of target in arr (sorted).
int lowerBound(int[] arr, int target) {
    int low = 0, high = arr.length;
    while (low < high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] < target)
            low = mid + 1;
        else
            high = mid;
    }
    return low;
}

```

----------

## ✅ Upper Bound:

> The **upper bound of a target** is the index of the first element strictly greater than the target.

```java
// Returns the index of the upper bound of target in arr (sorted).
int upperBound(int[] arr, int target) {
    int low = 0, high = arr.length;
    while (low < high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] <= target)
            low = mid + 1;
        else
            high = mid;
    }
    return low;
}

```

----------

✅ **Key Notes:**

-   Both functions work by adjusting `low` and `high` so that they converge to the correct bound.
    
-   The final value of `low` is returned directly.
    

