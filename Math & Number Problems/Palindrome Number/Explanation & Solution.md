# Explanation: Palindrome Number

**Problem:** [Palindrome Number](https://leetcode.com/problems/palindrome-number)

**Difficulty:** Easy

---

## Description

Given an integer `x`, return `true` if `x` is a **palindrome**, and `false` otherwise.

A palindrome is a number that reads the same backward as forward.  
For example, `121` is a palindrome while `123` is not.

---

## Examples

**Example 1**  
**Input:** `x = 121`  
**Output:** `true`

**Example 2**  
**Input:** `x = -121`  
**Output:** `false`  
**Explanation:** Reads `121-` from right to left — not the same.

**Example 3**  
**Input:** `x = 10`  
**Output:** `false`  
**Explanation:** Reads `01` from right to left.

---

## Approach

To check if a number is a palindrome:

1. Store the original number in a temporary variable.
2. Reverse the number by extracting digits using `% 10` and building the reversed number.
3. Compare the reversed number with the original:
   - If they are equal → it's a palindrome.
   - Otherwise → it's not.

💡 Note: We only reverse the number and **do not convert it to a string**, which is more efficient and avoids extra space.

---

## Time and Space Complexity

- **Time Complexity:** O(log₁₀(n)) – we process each digit once.
- **Space Complexity:** O(1) – only a few variables are used.

---

## Code (Java)

```java
class Solution {
    public boolean isPalindrome(int x) {
        int temp = x;
        int y = 0;
        while (temp > 0) {
            y = y * 10 + temp % 10;
            temp /= 10;
        }
        return y == x;
    }
}
