
# 📚 Trie-2 Data Structure — Java Implementation

## 📌 Overview

An enhanced Trie implementation that supports:

- Tracking:
  - **Number of times a word has been inserted**
  - **Number of words starting with a given prefix**
  
- Functions:
  - `insert(String word)`
  - `countWordsEqualTo(String word)`
  - `countWordsStartingWith(String prefix)`
  - `erase(String word)` — deletes a single occurrence


## 📌 Code

```java
class Trie2 {
    private class Node {
        private Node[] links = new Node[26];
        private int wordCount = 0;
        private int prefixCount = 0;

        public boolean containsKey(char ch) {
            return links[ch - 'a'] != null;
        }

        public Node get(char ch) {
            return links[ch - 'a'];
        }

        public void put(char ch, Node node) {
            links[ch - 'a'] = node;
        }

        public void increasePrefix() {
            prefixCount++;
        }

        public void decreasePrefix() {
            prefixCount--;
        }

        public int getPrefixCount() {
            return prefixCount;
        }

        public void increaseWordCount() {
            wordCount++;
        }

        public void decreaseWordCount() {
            wordCount--;
        }

        public int getWordCount() {
            return wordCount;
        }
    }

    private Node root;

    public Trie2() {
        root = new Node();
    }

    // Insert word into Trie
    public void insert(String word) {
        if (word == null || word.isEmpty()) return;

        Node node = root;
        for (int i = 0; i < word.length(); i++) {
            char ch = word.charAt(i);
            if (!node.containsKey(ch)) {
                node.put(ch, new Node());
            }
            node = node.get(ch);
            node.increasePrefix();
        }
        node.increaseWordCount();
    }

    // Count how many times word exists
    public int countWordsEqualTo(String word) {
        if (word == null || word.isEmpty()) return 0;

        Node node = root;
        for (int i = 0; i < word.length(); i++) {
            char ch = word.charAt(i);
            if (!node.containsKey(ch)) {
                return 0;
            }
            node = node.get(ch);
        }
        return node.getWordCount();
    }

    // Count how many words start with given prefix
    public int countWordsStartingWith(String prefix) {
        if (prefix == null || prefix.isEmpty()) return 0;

        Node node = root;
        for (int i = 0; i < prefix.length(); i++) {
            char ch = prefix.charAt(i);
            if (!node.containsKey(ch)) {
                return 0;
            }
            node = node.get(ch);
        }
        return node.getPrefixCount();
    }

    // Erase one occurrence of word from Trie
    public void erase(String word) {
        if (word == null || word.isEmpty()) return;

        Node node = root;
        for (int i = 0; i < word.length(); i++) {
            char ch = word.charAt(i);
            if (!node.containsKey(ch)) {
                return;  // word path broken — nothing to erase
            }
            node = node.get(ch);
            node.decreasePrefix();
        }
        node.decreaseWordCount();
    }
}


```



## 📖 Use Cases

- **Word frequency counting**
- **Autocomplete systems with frequency weighting**
- **Spellcheck with multiple occurrences**
- **Auto-delete logic**
- **Word prefix search optimizations**
- **Tracking and managing duplicate words**

---

## ⚠️ Cautions

- Only handles **lowercase English letters `a-z`**
- No support for uppercase, digits, or symbols
- Not thread-safe for concurrent operations
- `erase()` reduces counts but does not physically delete nodes; structure remains

---

## 📊 Time Complexity

| Operation               | Time Complexity |
|:------------------------|:----------------|
| `insert()`                | O(L) |
| `countWordsEqualTo()`     | O(L) |
| `countWordsStartingWith()`| O(L) |
| `erase()`                 | O(L) |

Where **L** is the length of the word/prefix.

---

## 📦 Space Complexity

O(N × L) — where **N** is the number of unique words inserted and **L** is the average word length.

---

## 📌 Example Usage

```java
Trie2 trie = new Trie2();

trie.insert("apple");
trie.insert("apple");
trie.insert("app");

System.out.println(trie.countWordsEqualTo("apple"));   // 2
System.out.println(trie.countWordsStartingWith("app"));// 3

trie.erase("apple");
System.out.println(trie.countWordsEqualTo("apple"));   // 1
System.out.println(trie.countWordsStartingWith("app"));// 2

```




