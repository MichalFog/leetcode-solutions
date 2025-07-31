# **Explanation: Find the Index of the First Occurrence in a String**

## **Problem:** [Find the Index of the First Occurrence in a String – LeetCode](https://leetcode.com/problems/find-the-index-of-the-first-occurrence-in-a-string/)

### **Difficulty Level:** Easy

---

## **Description**  
Given two strings `needle` and `haystack`, return the index of the first occurrence of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.

---

## **Examples**

**Example 1**  
**Input:** `haystack = "sadbutsad"`, `needle = "sad"`  
**Output:** `0`  
**Explanation:** The first occurrence of `"sad"` is at index `0`.

**Example 2**  
**Input:** `haystack = "leetcode"`, `needle = "leeto"`  
**Output:** `-1`  
**Explanation:** `"leeto"` is not present in `"leetcode"`.

---

## **Approach**

We slide a window of size equal to the length of `needle` across `haystack`:

- Loop from index `0` to `haystack.length() - needle.length()`.
- At each step, extract the substring from `haystack` of size equal to `needle` and compare it.
- If it matches, return the current index.
- If no match is found, return `-1`.

This is a straightforward brute-force implementation.

---

## **Time Complexity:**  
- **O(n * m)** in the worst case where `n` is the length of `haystack` and `m` is the length of `needle`.

## **Space Complexity:**  
- **O(1)** – Constant space used (only pointers and substrings).

---

## **Code (Java)**

```java
class Solution {
    public int strStr(String haystack, String needle) {
       for(int i = 0, j = needle.length(); j <= haystack.length(); i++, j++){
           if(haystack.substring(i, j).equals(needle))
               return i;
       }
       return -1;
    }
}
