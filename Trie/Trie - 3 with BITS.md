

## 📚 Maximum XOR of Two Numbers in an Array — Java (Bit Trie)

This project implements an efficient solution to find the maximum XOR of any two numbers in an array using a **Bitwise Trie (Prefix Tree)**. It optimizes the brute-force O(N²) approach down to O(N) time.

----------

## 📦 Features

-   Trie with 0-1 bits representation
    
-   Supports efficient insert and max XOR query operations
    
-   Optimized for 32-bit integers
    
-   Clean, modular, and defensive code
    

----------

## 📊 Time & Space Complexity

Operation

Time Complexity

Space Complexity

`insert(num)`

O(32) = O(1)

O(32 × N) = O(N)

`getMax(num)`

O(32) = O(1)

—

`findMaximumXOR(nums)`

O(N × 32) = O(N)

O(32 × N) = O(N)

👉 Where **N** is the number of elements in the array.

----------

## 📌 Code

```java
class Trie {
    private class Node {
        private Node[] links = new Node[2];

        public boolean containsKey(int i) {
            return links[i] != null;
        }

        public Node get(int i) {
            return links[i];
        }

        public void put(int i, Node node) {
            links[i] = node;
        }
    }

    private Node root;

    public Trie() {
        root = new Node();
    }

    // Insert number into Trie bit by bit (from MSB to LSB)
    public void insert(int num) {
        Node node = root;
        for (int i = 31; i >= 0; i--) {
            int bit = (num >> i) & 1;
            if (!node.containsKey(bit)) {
                node.put(bit, new Node());
            }
            node = node.get(bit);
        }
    }

    // Find maximum XOR of num with any number present in the Trie
    public int getMax(int num) {
        Node node = root;
        int max = 0;
        for (int i = 31; i >= 0; i--) {
            int bit = (num >> i) & 1;
            if (node.containsKey(1 - bit)) {
                max |= (1 << i);
                node = node.get(1 - bit);
            } else {
                node = node.get(bit);
            }
        }
        return max;
    }
}

class Solution {
    public int findMaximumXOR(int[] nums) {
        Trie trie = new Trie();
        for (int num : nums) trie.insert(num);

        int max = 0;
        for (int num : nums) {
            int curr = trie.getMax(num);
            if (curr > max) max = curr;
        }
        return max;
    }
}

```

----------

## 📖 Use Cases

-   **Find maximum XOR pair** in a given array
    
-   Classic bitwise optimization problem
    
-   Competitions like Codeforces, AtCoder, or LeetCode (Problem 421)
    
-   Any problem needing optimized bit-level pairing or comparisons
    

----------

## ⚠️ Cautions

-   Works for **32-bit non-negative integers only**
    
-   No delete operation — this Trie is for insert and query operations only
    
-   Not thread-safe for concurrent operations
    

----------

## 📦 Example

```java
int[] nums = {3, 10, 5, 25, 2, 8};
Solution sol = new Solution();
System.out.println(sol.findMaximumXOR(nums));  // Output: 28

```

**Explanation:**  
5 ⊕ 25 = 28 is the maximum possible XOR among any pair in the array.

----------
