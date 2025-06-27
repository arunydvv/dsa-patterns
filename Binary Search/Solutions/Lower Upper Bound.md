
# 📚 Lower Bound and Upper Bound in a Sorted Array using Binary Search (Java)

## ✅ Lower Bound:
> The **lower bound of a target** is the index of the first element greater than or equal to the target.

```java
// Returns the index of the lower bound of target in arr (sorted), or -1 if no such element exists.
int lowerBound(int[] arr, int target) {
    int low = 0, high = arr.length - 1;
    int ans = -1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (arr[mid] >= target) {
            ans = mid;          // possible lower bound
            high = mid - 1;
        } else {
            low = mid + 1;
        }
    }

    return ans;
}

```

----------

## ✅ Upper Bound:

> The **upper bound of a target** is the index of the first element strictly greater than the target.

```java
// Returns the index of the upper bound of target in arr (sorted), or -1 if no such element exists.
int upperBound(int[] arr, int target) {
    int low = 0, high = arr.length - 1;
    int ans = -1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (arr[mid] > target) {
            ans = mid;          // possible upper bound
            high = mid - 1;
        } else {
            low = mid + 1;
        }
    }

    return ans;
}

```

----------

---
