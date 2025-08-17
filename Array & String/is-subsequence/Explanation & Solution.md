# **Explanation: Is Subsequence**

## **Problem:** [Is Subsequence – LeetCode](https://leetcode.com/problems/is-subsequence/)

**Difficulty:** Easy  
**Topic:** Two Pointers, String

---

## **Description**  
Given two strings `s` and `t`, determine if `s` is a subsequence of `t`.  
A subsequence is a sequence that can be derived from another string by deleting some (or no) characters without changing the relative order.

---

## **Examples**

**Example 1**  
**Input:** `s = "abc"`, `t = "ahbgdc"`  
**Output:** `true`  
**Explanation:** You can obtain `"abc"` by deleting letters from `t` while maintaining order.

**Example 2**  
**Input:** `s = "axc"`, `t = "ahbgdc"`  
**Output:** `false`

---

## **Approach**

We use a **single pointer** to traverse `s`, scanning through `t`:

1. Initialize `indexS = 0` — position in `s`.
2. Loop through each character `t[i]` in `t`:
   - If `t[i] == s[indexS]`, increment `indexS`.
   - If `indexS == s.length()`, we've matched all characters.
3. If after scanning `t`, `indexS == s.length()` → return `true`; else → `false`.

This effectively "chases" each character in `s` through `t`.

---

## **Time and Space Complexity**

- **Time Complexity:** `O(n + m)`, where `n = s.length()` and `m = t.length()`  
- **Space Complexity:** `O(1)` — only a few variables are used.

---

## **Code (Java)**

```java
class Solution {
    public boolean isSubsequence(String s, String t) {
        int indexS = 0;
        int lenS = s.length();

        for (int i = 0; i < t.length() && indexS < lenS; i++) {
            if (t.charAt(i) == s.charAt(indexS)) {
                indexS++;
            }
        }

        return indexS == lenS;
    }
}
