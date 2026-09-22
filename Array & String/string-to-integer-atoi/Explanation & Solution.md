# Explanation: String to Integer (atoi)

## Problem: [String to Integer (atoi) – LeetCode](https://leetcode.com/problems/string-to-integer-atoi/description/)

Difficulty: Medium  
Topic: String

* * *

## Description

Implement the `myAtoi(string s)` function, which converts a string to a 32-bit signed integer.

The conversion follows these rules:

1. Ignore leading spaces.
2. Check for an optional `+` or `-` sign.
3. Read consecutive digits until a non-digit character is found.
4. If no digits are found, return `0`.
5. If the number is outside the 32-bit signed integer range `[-2³¹, 2³¹ - 1]`, clamp it to the nearest boundary.

The valid range is:

- `int.MinValue = -2147483648`
- `int.MaxValue = 2147483647`

* * *

## Examples

### Example 1

Input: `s = "42"`  
Output: `42`

### Example 2

Input: `s = "   -42"`  
Output: `-42`

### Example 3

Input: `s = "4193 with words"`  
Output: `4193`

The conversion stops when the first non-digit character is reached.

### Example 4

Input: `s = "words and 987"`  
Output: `0`

The first non-space character is not a sign or a digit, so no number can be parsed.

### Example 5

Input: `s = "-91283472332"`  
Output: `-2147483648`

The value is smaller than `int.MinValue`, so it is clamped to the minimum 32-bit integer.

* * *

## Approach

### Optimal Solution – Single Pass

We can solve the problem by scanning the string from left to right.

1. **Skip leading spaces**
   - Move the index forward while the current character is `' '`.

2. **Determine the sign**
   - If the current character is `'-'`, the number is negative.
   - If it is `'+'`, the number is positive.
   - If there is no sign, assume the number is positive.

3. **Read the digits**
   - While the current character is a digit, convert it to its numeric value.
   - Build the number using:
     `result = result * 10 + digit`

4. **Handle overflow**
   - We use `long` while building the number so that we can temporarily store values larger than the `int` range.
   - If the final value is greater than `int.MaxValue`, return `int.MaxValue`.
   - If it is smaller than `int.MinValue`, return `int.MinValue`.

5. **Stop at the first non-digit**
   - Once a non-digit character is reached, ignore the rest of the string.

This is a single scan through the string, so the solution is efficient.

* * *

## Time & Space Complexity

- **Time Complexity:** `O(n)` — we scan the string once.
- **Space Complexity:** `O(1)` — only a few variables are used.

* * *

## Code (C#)

```csharp
public class Solution
{
    public int MyAtoi(string s)
    {
        int i = 0;
        int sign = 1;
        long result = 0;

        // 1. Skip leading spaces
        while (i < s.Length && s[i] == ' ')
        {
            i++;
        }

        // 2. Check the sign
        if (i < s.Length && (s[i] == '+' || s[i] == '-'))
        {
            if (s[i] == '-')
            {
                sign = -1;
            }

            i++;
        }

        // 3. Read digits
        while (i < s.Length && char.IsDigit(s[i]))
        {
            result = result * 10 + (s[i] - '0');

            // 4. Check for overflow
            long signedResult = result * sign;

            if (signedResult > int.MaxValue)
            {
                return int.MaxValue;
            }

            if (signedResult < int.MinValue)
            {
                return int.MinValue;
            }

            i++;
        }

        return (int)(result * sign);
    }
}
```
