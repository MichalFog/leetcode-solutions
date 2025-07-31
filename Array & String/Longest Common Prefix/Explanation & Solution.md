# Explanation: Longest Common Prefix

**Problem:** [Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix)

**Difficulty:** Easy

---

## Description

Write a function to find the **longest common prefix string** amongst an array of strings.

If there is no common prefix, return an empty string `""`.

---

## Examples

**Example 1**  
**Input:** `["flower","flow","flight"]`  
**Output:** `"fl"`

**Example 2**  
**Input:** `["dog","racecar","car"]`  
**Output:** `""`  
**Explanation:** There is no common prefix among the input strings.

---

## Approach

We take the **first string as the initial prefix** and compare it with each string in the array:

- While the current string **does not start with the prefix**, we shorten the prefix from the end.
- If the prefix becomes empty at any point, we return `""`.

This approach guarantees that the final prefix is common to all strings in the array.

---

## Time and Space Complexity

- **Time Complexity:** O(S), where `S` is the sum of all characters in all strings.
- **Space Complexity:** O(1) – only a few string variables are used.

---

## Code (Java)

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) return "";

        String prefix = strs[0];

        for (int i = 1; i < strs.length; i++) {
            while (!strs[i].startsWith(prefix)) {
                prefix = prefix.substring(0, prefix.length() - 1);
                if (prefix.isEmpty()) return "";
            }
        }

        return prefix;
    }
}
```
