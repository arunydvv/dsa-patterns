
# 📖 Take K of Each Character From Left and Right (LeetCode 2516)

**Problem Link:** [https://leetcode.com/problems/take-k-of-each-character-from-left-and-right/](https://leetcode.com/problems/take-k-of-each-character-from-left-and-right/)



## 📜 Problem Statement:

You are given a string `s` containing only characters `'a'`, `'b'`, and `'c'`. You can take characters from the **start and/or end** of the string.  
Your goal is to take at least `k` of each character.  
Return the minimum number of characters you need to take, or `-1` if impossible.

----------

## 📊 Approaches (In Increasing Order of Optimisation)

----------

### 1️⃣ Brute-Force by All Splits (TLE)

**Idea:**

-   Try every possible split: pick `l` characters from the start and `r` from the end.
    
-   Check whether combined characters satisfy the requirement.
    
-   Track minimal total picks.
    

**Time Complexity:** `O(n²)`  
**Space Complexity:** `O(1)`

✅ Impractical for large `n`.

----------

### 2️⃣ Prefix + Suffix Preprocessing + Binary Search

**Idea:**

-   Precompute prefix counts and suffix counts of `a`, `b`, `c`.
    
-   For every possible number of characters to pick from the left (`l`), use **binary search** to find minimal number from the right (`r`) such that combined counts meet the requirement.
    

**Time Complexity:** `O(n log n)`  
**Space Complexity:** `O(n)`

✅ Much faster than brute force.

----------

### 3️⃣ Sliding Window (Optimal)

**Idea:**

-   Reverse the problem: find the **maximum length middle subarray you can skip** so that the characters outside it still satisfy `k` for each character.
    
-   Use a **sliding window** to track possible middle substrings.
    
-   Answer = `n - length of maximum skippable window`.
    

**Time Complexity:** `O(n)`  
**Space Complexity:** `O(1)`

✅ Optimal linear solution.

----------

## 📦 Code (Approach-wise)

----------

### 1️⃣ Brute-Force by All Splits (TLE)

```java
public int takeCharactersBrute(String s, int k) {
    int n = s.length();
    int[] total = new int[3];
    for (char c : s.toCharArray()) total[c - 'a']++;
    if (total[0] < k || total[1] < k || total[2] < k) return -1;

    int res = n;
    for (int l = 0; l <= n; l++) {
        int[] cnt = new int[3];
        for (int i = 0; i < l; i++) cnt[s.charAt(i) - 'a']++;
        for (int r = n; r >= l; r--) {
            if (r < n) cnt[s.charAt(r) - 'a']++;
            if (cnt[0] >= k && cnt[1] >= k && cnt[2] >= k) {
                res = Math.min(res, l + n - r);
            }
        }
    }
    return res;
}

```

----------

### 2️⃣ Prefix + Suffix Preprocessing + Binary Search

```java
public int takeCharactersPrefixSuffix(String s, int k) {
    int n = s.length();
    int[][] prefix = new int[n+1][3];
    int[][] suffix = new int[n+1][3];
    for (int i = 0; i < n; i++) {
        for (int c = 0; c < 3; c++) prefix[i+1][c] = prefix[i][c];
        prefix[i+1][s.charAt(i) - 'a']++;
    }
    for (int i = n-1; i >= 0; i--) {
        for (int c = 0; c < 3; c++) suffix[i][c] = suffix[i+1][c];
        suffix[i][s.charAt(i) - 'a']++;
    }

    if (prefix[n][0] < k || prefix[n][1] < k || prefix[n][2] < k) return -1;
    int res = Integer.MAX_VALUE;

    for (int l = 0; l <= n; l++) {
        int[] cnt = Arrays.copyOf(prefix[l], 3);
        int low = 0, high = n, validR = -1;
        while (low <= high) {
            int mid = (low + high) / 2;
            int[] sc = suffix[n - mid];
            if (cnt[0] + sc[0] >= k && cnt[1] + sc[1] >= k && cnt[2] + sc[2] >= k) {
                validR = mid;
                high = mid - 1;
            } else low = mid + 1;
        }
        if (validR != -1) res = Math.min(res, l + validR);
    }
    return res;
}

```

----------

### 3️⃣ Sliding Window (Optimal)

```java
public int takeCharacters(String s, int k) {
    int n = s.length();
    int[] total = new int[3];
    for (char c : s.toCharArray()) total[c - 'a']++;

    if (total[0] < k || total[1] < k || total[2] < k) return -1;

    int res = 0;
    int[] count = new int[3];
    for (int l = 0, r = 0; r < n; r++) {
        count[s.charAt(r) - 'a']++;
        while (count[0] > total[0] - k || count[1] > total[1] - k || count[2] > total[2] - k) {
            count[s.charAt(l) - 'a']--;
            l++;
        }
        res = Math.max(res, r - l + 1);
    }
    return n - res;
}

```



## ✅ Final Summary:


**Brute-Force by All Splits (TLE)**

`Time Complexity O(n²)`

`Space Complexity O(1)`

**Prefix + Suffix + Binary Search**

`Time Complexity O(n log n)`

`Space Complexity O(n)`

**Sliding Window (Optimal)**

`Time Complexity TC O(n)`

`Space Complexity O(1)`


