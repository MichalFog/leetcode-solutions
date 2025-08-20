# **Explanation: Greatest Common Divisor of Strings**

## **Problem:** [Greatest Common Divisor of Strings – LeetCode](https://leetcode.com/problems/greatest-common-divisor-of-strings/)

### **Difficulty Level:** Easy

---

## **Description**  
Given two strings `str1` and `str2`, return the **largest string `x`** such that `x` divides both `str1` and `str2`.  

A string `t` divides string `s` if `s = t + t + ... + t` (t concatenated multiple times).

---

## **Examples**

**Example 1**  
**Input:** `str1 = "ABCABC"`, `str2 = "ABC"`  
**Output:** `"ABC"`  
**Explanation:** `"ABC"` concatenated 2 times is `"ABCABC"`; it also divides `"ABC"` once.

**Example 2**  
**Input:** `str1 = "ABABAB"`, `str2 = "ABAB"`  
**Output:** `"AB"`  
**Explanation:** `"AB"` concatenated 3 times is `"ABABAB"` and concatenated 2 times is `"ABAB"`.

**Example 3**  
**Input:** `str1 = "LEET"`, `str2 = "CODE"`  
**Output:** `""`  
**Explanation:** There is no common string that can divide both.

---

## **Approach**

Key observations:

1. If `str1 + str2 != str2 + str1`, then no string can divide both (`return ""`).
2. Otherwise, the length of the greatest common divisor string is the **GCD of the lengths** of the two strings.

### **Steps**:

1. Check if concatenating `str1 + str2` equals `str2 + str1`. If not, return empty string.
2. Compute the GCD of the lengths of `str1` and `str2`.
3. Return the substring of `str1` from `0` to the GCD length.

---

## **Time and Space Complexity**

- **Time Complexity:** `O(n + m)` — concatenation check is linear in combined length; GCD calculation is `O(log(min(n, m)))`.  
- **Space Complexity:** `O(n + m)` — due to concatenation for the check.

---

## **Code (Java)**

```java
class Solution {
    public String gcdOfStrings(String str1, String str2) {
        if (!(str1 + str2).equals(str2 + str1))
            return "";
        return str1.substring(0, getNumOfDivide(str1.length(), str2.length()));
    }

    public int getNumOfDivide(int x, int y) {
        while (y != 0) {
            int temp = y;
            y = x % y;
            x = temp;
        }
        return x;
    }
}
