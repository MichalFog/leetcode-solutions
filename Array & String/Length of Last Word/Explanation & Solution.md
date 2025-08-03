# **Explanation: Length of Last Word**

## **Problem:** [Length of Last Word – LeetCode](https://leetcode.com/problems/length-of-last-word/)

### **Difficulty Level:** Easy

---

## **Description**  
Given a string `s` consisting of words and spaces, return the **length of the last word** in the string.

A word is a **maximal substring** consisting of non-space characters only.

---

## **Examples**

**Example 1**  
**Input:** `"Hello World"`  
**Output:** `5`  
**Explanation:** The last word is `"World"` and its length is `5`.

**Example 2**  
**Input:** `"   fly me   to   the moon  "`  
**Output:** `4`  
**Explanation:** The last word is `"moon"` and its length is `4`.

**Example 3**  
**Input:** `"luffy is still joyboy"`  
**Output:** `6`  
**Explanation:** The last word is `"joyboy"` and its length is `6`.

---

## **Approach**

We iterate **backwards** through the string:

1. Skip all trailing spaces.
2. Start counting characters until the next space or start of the string.
3. Return the count.

This approach avoids unnecessary string splitting and is highly efficient.

---

## **Time Complexity:**  
- **O(n)** – Where `n` is the length of the string.

## **Space Complexity:**  
- **O(1)** – Uses constant extra space.

---

## **Code (Java)**

```java
class Solution {
    public int lengthOfLastWord(String s) {
        int l = 0, i = s.length() - 1;

        // Skip trailing spaces
        while (i > 0 && s.charAt(i) == ' ') {
            i--;
        }

        // Count characters of the last word
        while (i >= 0 && s.charAt(i) != ' ') {
            i--;
            l++;
        }

        return l;
    }
}
