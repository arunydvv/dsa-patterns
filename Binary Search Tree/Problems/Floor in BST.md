
### ✅ Floor in a Binary Search Tree

**Problem:**  
Given a BST and a target value, find the floor of the target in the BST. The floor of the target is the greatest value in the BST that is less than or equal to the target. If no such value exists, return some indicator (like `-1` or `null`).

---

| Approach                      | Time Complexity | Space Complexity |
|-------------------------------|-----------------|------------------|
| **Recursive Search**           | O(h)            | O(h)             |
| **Iterative Search**           | O(h)            | O(1)             |

---

## Approach 1: Recursive Search

**Idea:**  
- If the current node is `null`, return -1 (or no floor found).  
- If the current node’s value equals the target, return it.  
- If current node’s value is greater than the target, recurse into the left subtree to find a smaller or equal value.  
- Else, recurse into the right subtree for potentially closer values <= target, but if none found there, the current node might be the floor.

**Code (Java):**
```java
class Solution {
    public int floorInBST(TreeNode root, int target) {
        if (root == null) return -1;

        if (root.val == target) return root.val;

        if (root.val > target) {
            return floorInBST(root.left, target);
        }

        // root.val < target
        int floorRight = floorInBST(root.right, target);
        if (floorRight <= target && floorRight != -1) return floorRight;
        else return root.val;
    }
}

```

**Time Complexity:** O(h)  
**Space Complexity:** O(h) due to recursion stack

----------

## Approach 2: Iterative Search

**Idea:**

-   Use a loop to traverse the BST starting from the root.
    
-   If current node value equals target, return it immediately.
    
-   If current node value is less than target, record current node as potential floor and move to right subtree to find closer floor.
    
-   Else move to left subtree.
    
-   Return the last recorded floor value.
    

**Code (Java):**

```java
class Solution {
    public int floorInBST(TreeNode root, int target) {
        int floor = -1;
        TreeNode curr = root;
        while (curr != null) {
            if (curr.val == target) {
                return curr.val;
            } else if (curr.val < target) {
                floor = curr.val;
                curr = curr.right;
            } else {
                curr = curr.left;
            }
        }
        return floor;
    }
}

```

**Time Complexity:** O(h)  
**Space Complexity:** O(1)

----------

### Notes:

-   The BST property helps prune the search space to O(h) instead of O(n).
    
-   The iterative approach is more space efficient.
    
-   You can adjust the return value (`-1`, `null`, or optional) depending on problem constraints.
    

----------

_Happy coding!_

