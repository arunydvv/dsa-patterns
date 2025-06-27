# 📚 Floor and Ceil in a Sorted Array using Binary Search (Java)

## ✅ Floor:
> The **floor of a target** in a sorted array is the **greatest element less than or equal to the target      value >= target**.

```java
// Returns the index of the floor of target in arr (sorted), or -1 if no floor exists.
int floor(int[] arr, int target) {
    int low = 0, high = arr.length - 1;
    int ans = -1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (arr[mid] <= target) {
            ans = mid;          // possible floor
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }

    return ans;
}

```

----------

## ✅ Ceil:

> The **ceil of a target** in a sorted array is the **smallest element greater than or equal to the target   value > target**.

```java
// Returns the index of the ceil of target in arr (sorted), or -1 if no ceil exists.
int ceil(int[] arr, int target) {
    int low = 0, high = arr.length - 1;
    int ans = -1;

    while (low <= high) {
        int mid = low + (high - low) / 2;

        if (arr[mid] >= target) {
            ans = mid;          // possible ceil
            high = mid - 1;
        } else {
            low = mid + 1;
        }
    }

    return ans;
}

```






