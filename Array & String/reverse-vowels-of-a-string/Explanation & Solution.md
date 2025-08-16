# Reverse Vowels of a String

**Link**: [LeetCode - Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)  
**Difficulty**: Easy  
**Topic**: String, Two Pointers  

---

## Description  
Given a string `s`, reverse only all the vowels in the string and return it.  
The vowels are `'a', 'e', 'i', 'o', 'u'`, and they can appear in both lower and upper cases.  

---

## Examples  

### Example 1
**Input**:  
s = "hello"
**Output**:  
"holle"

---

## Solution Approach  
We use **two pointers**:  
- One starts from the left and moves forward until it finds a vowel.  
- One starts from the right and moves backward until it finds a vowel.  
- Swap them, then move both pointers inward.  
- Continue until they meet.  

This solution is efficient because it scans each character at most once.  

---

## Complexity  
- **Time Complexity**: `O(n)` — each character is visited at most once.  
- **Space Complexity**: `O(n)` — due to using a `StringBuilder`.  

---

## Code (Java)
```java
class Solution {
    public String reverseVowels(String s) {
        if (s == null || s.length() == 0) return s;

        StringBuilder sb = new StringBuilder(s);
        int left = 0;
        int right = sb.length() - 1;

        while (left < right) {
            while (left < right && !isVowel(sb.charAt(left))) {
                left++;
            }

            while (left < right && !isVowel(sb.charAt(right))) {
                right--;
            }

            char temp = sb.charAt(left);
            sb.setCharAt(left, sb.charAt(right));
            sb.setCharAt(right, temp);

            left++;
            right--;
        }

        return sb.toString();
    }

    private boolean isVowel(char c) {
        return "aeiouAEIOU".indexOf(c) != -1;
    }
}
