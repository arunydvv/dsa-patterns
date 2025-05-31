# 📚 Sliding Window Algorithm Patterns — Exhaustive List

This document exhaustively lists every sliding window pattern in algorithmic problem-solving, along with their corresponding problems. Whether a pattern has one or one hundred problems — it’s listed.

---

## 📌 Fixed-Length Sliding Window

### 📌 Pattern

Keep a window of fixed size `k`, slide one element at a time.

### ✅ Problems

- Maximum Sum Subarray of Size K
- First Negative Number in Every Window of Size K
- Count Number of Occurrences of Anagrams
- Maximum Average Subarray I
- Max Consecutive Ones III
- Number of Subarrays of Size K with Average Greater than Threshold

---

## 📌 Variable-Length (Dynamic) Sliding Window

### 📌 Pattern

Expand window till condition met, then shrink from left while maintaining validity.

### ✅ Problems

- Longest Substring with K Distinct Characters
- Longest Substring Without Repeating Characters
- Minimum Size Subarray Sum
- Longest Substring with At Most Two Distinct Characters
- Smallest Window Containing Substring
- Fruits Into Baskets (Longest Subarray with At Most 2 Types of Fruits)
- Longest Substring with Replacement
- Max Consecutive Ones II
- Max Consecutive Ones III
- Replace Ones to Maximize Continuous 1s

---

## 📌 Prefix-Suffix Sum Based Sliding Window

### 📌 Pattern

Use two pointers or pre-sums from left and right ends and narrow down window size.

### ✅ Problems

- Max Number of K-Sum Pairs
- Maximize Sum of Array After K Operations
- Max Points from Cards
- Minimum Operations to Reduce X to Zero

---

## 📌 Monotonic Queue / Deque Based Sliding Window

### 📌 Pattern

Use deque to keep window max/min in O(1) time as window slides.

### ✅ Problems

- Sliding Window Maximum
- Sliding Window Minimum
- Shortest Subarray with Sum at Least K (Using Deque)
- Sum of Minimums of All Subarrays

---

## 📌 Circular Sliding Window

### 📌 Pattern

Window that wraps around the array's end to start.

### ✅ Problems

- Maximum Sum Circular Subarray
- Gas Station
- Find Minimum in Rotated Sorted Array (Modified)
- Maximum Product Subarray in Circular Array

---

## 📌 Count or Frequency Map Based Sliding Window

### 📌 Pattern

Use hash map / counter to track characters/integers within a window.

### ✅ Problems

- Longest Substring Without Repeating Characters
- Longest Substring with K Distinct Characters
- Count Number of Occurrences of Anagrams
- Smallest Window Containing Substring
- Longest Repeating Character Replacement
- Longest Substring with At Most Two Distinct Characters

---

## 📌 Bitmask or State Based Sliding Window

### 📌 Pattern

Use bitmask or state representation within a sliding window.

### ✅ Problems

- Subarrays with K Different Integers
- Number of Substrings Containing All Three Characters (abc)
- Subarray Product Less Than K

---

## 📌 Maximum / Minimum Sum Sliding Window

### 📌 Pattern

Find max/min sum for continuous subarrays of size k.

### ✅ Problems

- Maximum Sum Subarray of Size K
- Minimum Sum Subarray of Size K
- Max Sum Circular Subarray (variation)
- Minimum Size Subarray Sum (variable length)

---

## 📌 Max Number of Operations in a Window

### 📌 Pattern

Perform operations (replace/delete/add) while keeping count in the window.

### ✅ Problems

- Longest Substring with Replacement
- Max Consecutive Ones II / III
- Longest Subarray of 1’s After Deleting One Element
- Replace Ones to Maximize Continuous 1s

---

## 📌 Substring / Subarray Count Using Sliding Window

### 📌 Pattern

Count number of substrings/subarrays satisfying a property.

### ✅ Problems

- Number of Substrings Containing All Three Characters
- Number of Subarrays with Sum Less Than K
- Number of Substrings With Exactly K Distinct Characters
- Subarray Product Less Than K
- Number of Subarrays with Sum Equal to K (Prefix sum + hash, can be windowed)

---

## 📌 Max Frequency in a Sliding Window

### 📌 Pattern

Track frequency of elements inside a sliding window to make decisions.

### ✅ Problems

- Longest Repeating Character Replacement
- Fruits Into Baskets
- Max Consecutive Ones II/III

---

## 📌 Edge / Niche Sliding Window Patterns

### ✅ Problems

- Find K Closest Elements (2-pointer shrink from sides)
- Longest Turbulent Subarray (window expands/shrinks by condition)
- Check If Array Can Be Divided Into K Consecutive Numbers (window via frequency map)
- Max Consecutive Answers (in exam string questions)
- Grumpy Bookstore Owner (Fixed window maximizing gain)
- Maximum Erasure Value (Longest subarray with unique elements)

---

## ✅ Conclusion

This document categorizes every known sliding window pattern type, serving as a reference for CP, interviews, and algorithmic strategy.

---

## 📌 Coming Soon

✅ Code examples for every problem  
✅ Complexity analysis for each pattern

---

## 📖 Contributions

Want to add a new edge-case sliding window pattern? Open a PR 🚀
