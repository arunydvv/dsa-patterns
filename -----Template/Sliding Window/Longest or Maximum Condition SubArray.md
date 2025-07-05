
## 📦 Sliding Window Template: Longest / Maximum Condition SubArray

```java
public int longestSubarray(int[] nums, int k) {
    int left = 0, right = 0;
    int n = nums.length;
    int maxLen = 0;

    // Use variables to track window property
    int windowProperty = 0;

    for (right = 0; right < n; right++) {
        // Expand: include nums[right] into window
        windowProperty += nums[right];

        // Shrink: while window is invalid
        while (windowProperty > k) {
            // Remove nums[left] from window
            windowProperty -= nums[left];
            left++;
        }

        // Update maxLen if condition satisfied
        maxLen = Math.max(maxLen, right - left + 1);
    }

    return maxLen;
}

```

----------

## 📌 Key Components



`left` & `right`  : 2 pointers to represent the window boundaries

`windowProperty` : Tracks some property (like sum, count of distinct chars, flips etc.)

`while` loop :Shrinks the window until the constraint is satisfied

`maxLen` Keeps track of the maximum length seen so far



## 📖 Variants you can plug into this template:

### ✅ 1️⃣ Longest Subarray with Sum ≤ `k`

```java
while (windowSum > k) {
    windowSum -= nums[left];
    left++;
}
maxLen = Math.max(maxLen, right - left + 1);

```

### ✅ 2️⃣ Longest Substring with at most `k` distinct characters

```java
Map<Character, Integer> freq = new HashMap<>();
while (freq.size() > k) {
    char ch = s.charAt(left);
    freq.put(ch, freq.get(ch) - 1);
    if (freq.get(ch) == 0) freq.remove(ch);
    left++;
}
maxLen = Math.max(maxLen, right - left + 1);

```

### ✅ 3️⃣ Max Consecutive 1’s with at most one 0 flipped

```java
int zeros = 0;
while (zeros > 1) {
    if (nums[left] == 0) zeros--;
    left++;
}
maxLen = Math.max(maxLen, right - left + 1);

```

----------

## 📌 When to use this template:

✅ When you need:

-   A continuous subarray/substring
    
-   To track maximum or longest length satisfying a **window condition**
    
-   Efficient O(n) solution without nested loops
    

----------

## 📌 Time & Space Complexity:

-   **Time:** `O(n)` (both pointers traverse at most n elements)
    
-   **Space:** `O(1)` or `O(k)` if using HashMap for character frequency
    

----------

## 📦 Clean Generalized Template:

```java
int left = 0, right = 0;
for (right = 0; right < n; right++) {
    // Include nums[right] into window

    // While window invalid
    while (/* window property invalid */) {
        // Shrink window from left
        left++;
    }

    // Update result
    maxLen = Math.max(maxLen, right - left + 1);
}

```

----------

## 🔥 Pro Tip:

If you're asked for **smallest subarray** satisfying a condition — same template, but instead of `maxLen = Math.max(...)`, you'd track `minLen = Math.min(...)` and sometimes update result **inside the while loop when condition is satisfied**.

----------
