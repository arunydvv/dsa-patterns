
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
    static class Node{
        Node[] links = new Node[26];
        boolean flag = false;
        
        boolean containsKey(char ch){
            return links[ch -'a'] != null;
        }
        
        Node get(char ch){
            return links[ch - 'a'];
        }

        void put(char ch, Node node){
             links[ch - 'a'] = node;
        }
        
        void setEnd(){
            flag = true;   // means a word ends here
            // If apple ends at 'e' we look at links[e] node and if that is flag = true
            // that means apple is present in Trie 
        }
        
        boolean isEnd(){
            return flag;
        }        
    }
    
    
    private Node root;
    public Trie() {
        root = new Node();       
    }

    public void insert(String word) {
        Node current = root;
        for (int i = 0; i < word.length(); i++) {
            if (!current.containsKey(word.charAt(i))){
                current.put(word.charAt(i), new Node());
            }
            current = current.get(word.charAt(i));
        }
        current.setEnd();;
    }

    public boolean search(String word) {
        Node current = root;
        for (int i = 0; i < word.length(); i++) {
            if (!current.containsKey(word.charAt(i))) return false;
            current = current.get(word.charAt(i));
        }
        return current.isEnd();
    }

    public boolean startsWith(String prefix) {
        Node current = root;
        for (int i = 0; i < prefix.length(); i++) {
            if (!current.containsKey(prefix.charAt(i))) return false;
            current = current.get(prefix.charAt(i));
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
