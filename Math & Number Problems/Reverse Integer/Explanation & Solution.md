
# Explanation: Reverse Integer

**Problem:** [Reverse Integer](https://leetcode.com/problems/reverse-integer)

**Difficulty:** Medium

---

## Description

Given a signed 32-bit integer `x`, return `x` with its digits reversed.  
If reversing `x` causes the value to go outside the signed 32-bit integer range `[-2³¹, 2³¹ - 1]`, return `0`.

---

## Examples

**Example 1**  
**Input:** `x = 123`  
**Output:** `321`

**Example 2**  
**Input:** `x = -123`  
**Output:** `-321`

**Example 3**  
**Input:** `x = 120`  
**Output:** `21`

**Example 4**  
**Input:** `x = 0`  
**Output:** `0`

---

## Approach

We extract the digits of `x` one by one using modulus and division operations.  
While constructing the reversed number, we check for **overflow** and return `0` if the reversed number would exceed 32-bit signed integer limits.

### Overflow Handling:
- If `reversed > Integer.MAX_VALUE / 10` or
- If `reversed == Integer.MAX_VALUE / 10` and the next digit would cause overflow (i.e., digit > 7)
- Similarly for negative limit: `reversed < Integer.MIN_VALUE / 10` or digit < -8

This protects against cases like reversing `1534236469` which would overflow.

---

## Time and Space Complexity

- **Time Complexity:** O(log₁₀(x)) – because we're processing each digit.
- **Space Complexity:** O(1) – we only use a few integer variables.

---

## Code (Java)

```java
public class Solution {
    public int reverse(int x) {
        int reversed = 0;

        while (x != 0) {
            int digit = x % 10;
            x = x / 10;

            if (reversed > Integer.MAX_VALUE / 10 || 
                (reversed == Integer.MAX_VALUE / 10 && digit > 7)) {
                return 0;
            }
            if (reversed < Integer.MIN_VALUE / 10 || 
                (reversed == Integer.MIN_VALUE / 10 && digit < -8)) {
                return 0;
            }

            reversed = reversed * 10 + digit;
        }

        return reversed;
    }
}
