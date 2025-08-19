# **Explanation: Add Strings**

## **Problem:** [Add Strings – LeetCode](https://leetcode.com/problems/add-strings/)

**Difficulty:** Easy  
**Topic:** String, Math

---

## **Description**  
Given two non-negative integers `num1` and `num2` represented as strings, return the sum of `num1` and `num2`, also as a string.

You must **not convert** the inputs directly to integers or use any built-in large number libraries.

---

## **Examples**

**Example 1**  
**Input:**  
num1 = "11", num2 = "123"

**Output:**  
"134"


**Example 2**  
**Input:**  
num1 = "456", num2 = "77"
**Output:**  
"533"

**Example 3**  
**Input:**  
num1 = "0", num2 = "0"
**Output:**  
"0"

---

## **Approach**

We simulate **manual digit-by-digit addition**, from right to left, managing carry as we go:

1. Initialize indices `i` and `j` to the end of `num1` and `num2`, respectively, and `carry = 0`.
2. Loop while `i >= 0 || j >= 0 || carry != 0`:
   - Extract digits `x` from `num1[i]` and `y` from `num2[j]` (or 0 if out of range).
   - Compute `sum = x + y + carry`.
   - Update `carry = sum / 10`.
   - Append `sum % 10` to the result builder.
3. Reverse the builder's content and return the resulting string.

This method efficiently handles very large numerical strings without numeric overflow.

---

## **Time and Space Complexity**

- **Time Complexity:** `O(n + m)` — where `n` and `m` are the lengths of `num1` and `num2`.
- **Space Complexity:** `O(n + m)` for the result and internal `StringBuilder`.

---

## **Code (Java)**

```java
class Solution {
    public String addStrings(String num1, String num2) {
        StringBuilder sb = new StringBuilder();
        int i = num1.length() - 1;
        int j = num2.length() - 1;
        int carry = 0;

        while (i >= 0 || j >= 0 || carry != 0) {
            int x = (i >= 0) ? num1.charAt(i) - '0' : 0;
            int y = (j >= 0) ? num2.charAt(j) - '0' : 0;
            int sum = x + y + carry;
            carry = sum / 10;
            sb.append(sum % 10);
            i--;
            j--;
        }

        return sb.reverse().toString();
    }
}
