# **Explanation: Valid Palindrome**

## **Problem:** [Valid Palindrome – LeetCode](https://leetcode.com/problems/valid-palindrome/)

### **Difficulty Level:** Easy

---

## **Description**  
Given a string `s`, determine if it is a **palindrome**, considering only **alphanumeric characters** and ignoring cases.  
A palindrome reads the same forward and backward.

---

## **Examples**

**Example 1**  
**Input:** `"A man, a plan, a canal: Panama"`  
**Output:** `true`  
**Explanation:** After removing non-alphanumeric characters and ignoring case, the string is `"amanaplanacanalpanama"` which is a palindrome.

**Example 2**  
**Input:** `"race a car"`  
**Output:** `false`  
**Explanation:** After cleaning, it becomes `"raceacar"` which is not a palindrome.

**Example 3**  
**Input:** `" "`  
**Output:** `true`  
**Explanation:** An empty string after cleaning is considered a palindrome.

---

## **Approach**

### **Idea:**  
Use **two pointers** — one starting from the left and the other from the right.  
Skip all characters that are **not letters or digits**.  
Compare characters (case-insensitive) from both ends until they meet.

---

## **Steps**:
1. Initialize two pointers: `left = 0` and `right = s.length() - 1`.
2. While `left < right`:
   - Move `left` forward if the current character is not alphanumeric.
   - Move `right` backward if the current character is not alphanumeric.
   - Compare the lowercase versions of the characters.
   - If they are not equal → return `false`.
3. If the loop ends without mismatches → return `true`.

---

## **Time and Space Complexity**

- **Time Complexity:** `O(n)` — we visit each character at most once.
- **Space Complexity:** `O(1)` — no extra data structures are needed.

---

## **Code (Java)**

```java
public class Solution {
    public boolean isPalindrome(String s) {
        int left = 0;
        int right = s.length() - 1;

        while (left < right) {
            while (left < right && !Character.isLetterOrDigit(s.charAt(left))) {
                left++;
            }

            while (left < right && !Character.isLetterOrDigit(s.charAt(right))) {
                right--;
            }

            if (Character.toLowerCase(s.charAt(left)) != Character.toLowerCase(s.charAt(right))) {
                return false;
            }

            left++;
            right--;
        }

        return true;
    }
}
