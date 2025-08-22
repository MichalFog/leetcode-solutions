
# Explanation: Valid Parentheses

**Problem:** [Valid Parentheses](https://leetcode.com/problems/valid-parentheses)

**Difficulty:** Easy

---

## Description

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['`, and `']'`, determine if the input string is **valid**.

A string is valid if:
- Open brackets are closed by the same type of brackets.
- Open brackets are closed in the correct order.
- Every closing bracket has a corresponding opening bracket.

---

## Examples

**Example 1**  
**Input:** `s = "()"`  
**Output:** `true`

**Example 2**  
**Input:** `s = "()[]{}"`  
**Output:** `true`

**Example 3**  
**Input:** `s = "(]"`  
**Output:** `false`

**Example 4**  
**Input:** `s = "([)]"`  
**Output:** `false`

**Example 5**  
**Input:** `s = "{[]}"`  
**Output:** `true`

---

## Approach

We use a **stack** to track expected closing brackets:

1. Traverse the string character by character.
2. If it's an opening bracket:
   - Push its corresponding **closing** bracket onto the stack.
3. If it's a closing bracket:
   - Check if the stack is empty or if the top doesn't match the current character.
   - If so → invalid.
4. At the end, if the stack is empty → all brackets were matched correctly.

---

## Time and Space Complexity

- **Time Complexity:** O(n) – where `n` is the length of the string.
- **Space Complexity:** O(n) – for the stack in the worst case.

---

## Code (Java)

```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();

        for (char ch : s.toCharArray()) {
            if (ch == '(') stack.push(')');
            else if (ch == '{') stack.push('}');
            else if (ch == '[') stack.push(']');
            else {
                if (stack.isEmpty() || stack.pop() != ch) {
                    return false;
                }
            }
        }

        return stack.isEmpty();
    }
}
