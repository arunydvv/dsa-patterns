
# 📚 Trie Data Structure (Prefix Tree) — Java Implementation


This project implements a Trie (Prefix Tree) with:

- A nested `Node` class containing:
  - `links[26]` for 26 lowercase English letters
  - `flag` to mark the end of a word
  - Utility methods:
    - `containsKey(char ch)`
    - `get(char ch)`
    - `put(char ch, Node node)`
    - `setEnd()`
    - `isEnd()`

- A main `Trie` class providing:
  - `insert(String word)` — inserts a word into the Trie
  - `search(String word)` — checks if a word exists in the Trie
  - `startsWith(String prefix)` — checks if any word in the Trie starts with the given prefix

---

```java
class Trie {
    private class Node {
        private Node[] links = new Node[26];
        private boolean flag = false;

        public boolean containsKey(char ch) {
            return links[ch - 'a'] != null;
        }

        public Node get(char ch) {
            return links[ch - 'a'];
        }

        public void put(char ch, Node node) {
            links[ch - 'a'] = node;
        }

        public void setEnd() {
            flag = true;
        }

        public boolean isEnd() {
            return flag;
        }
    }

    private Node root;

    public Trie() {
        root = new Node();
    }

    public void insert(String word) {
        Node node = root;
        for (char ch : word.toCharArray()) {
            if (!node.containsKey(ch)) {
                node.put(ch, new Node());
            }
            node = node.get(ch);
        }
        node.setEnd();
    }

    public boolean search(String word) {
        Node node = root;
        for (char ch : word.toCharArray()) {
            if (!node.containsKey(ch)) {
                return false;
            }
            node = node.get(ch);
        }
        return node.isEnd();
    }

    public boolean startsWith(String prefix) {
        Node node = root;
        for (char ch : prefix.toCharArray()) {
            if (!node.containsKey(ch)) {
                return false;
            }
            node = node.get(ch);
        }
        return true;
    }
}

```

## ⚠️ Cautions

- **Only handles lowercase English letters `a` to `z`**.  
  To extend it for uppercase, numerics, or Unicode, modify the `links` array size and char mapping accordingly.
  
- **No deletion method implemented** — this is a read/insert-only Trie.

- **Fixed alphabet size (26)** — make sure the input constraints match this.

- **Cant safely erase here** 

- **Not thread-safe** — avoid concurrent access without synchronization in multi-threaded environments.

---

## 📖 Use Cases

- **Autocomplete systems** — suggest possible completions for a given prefix.
- **Spell checkers** — quickly verify if a word exists.
- **Word search puzzles** — efficiently check word presence in a grid.
- **IP routing (longest prefix match)** — with modifications.
- **Text prediction engines**.
- **Dictionary applications**.

---

## 📊 Time Complexity

| Operation   | Time Complexity |
|:------------|:----------------|
| `insert()`   | O(L) |
| `search()`   | O(L) |
| `startsWith()` | O(L) |

Where **L** is the length of the word/prefix.

---

## 📦 Space Complexity

O(N × L) — where **N** is the number of words inserted, and **L** is average word length.

---

## 📌 Example Usage

```java
Trie trie = new Trie();
trie.insert("apple");
System.out.println(trie.search("apple"));   // true
System.out.println(trie.search("app"));     // false
System.out.println(trie.startsWith("app")); // true
trie.insert("app");
System.out.println(trie.search("app"));     // true

```
