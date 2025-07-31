# **Explanation: Longest Substring Without Repeating Characters**

## **Problem:** [Longest Substring Without Repeating Characters - LeetCode](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

### **Difficulty Level:** Medium

---

## **Description**  
Given a string `s`, find the length of the **longest substring** without repeating characters.

---

## **Example**

**Input:** `s = "abcabcbb"`  
**Output:** `3`  
**Explanation:**  
```
Substring: "abc" → length = 3
```

**Input:** `s = "bbbbb"`  
**Output:** `1`  
**Explanation:**  
```
Substring: "b" → length = 1
```

**Input:** `s = "pwwkew"`  
**Output:** `3`  
**Explanation:**  
```
Substring: "wke" → length = 3  
Note: The answer must be a substring, not a subsequence.
```

---

## **Approach**

We use the **sliding window** technique with a `HashSet` to track characters in the current window:

1. Use two pointers: `left` and `right` to define the current window.
2. Iterate with `right` through the string:
   - If `s[right]` is already in the `seen` set, move `left` forward and remove characters from `seen` until `s[right]` is not in the set.
3. Add `s[right]` to the set.
4. Update the maximum window size (`maxLength`) as `right - left + 1`.

This way we maintain a window of **unique characters only**.

---

## **Time Complexity**
- **O(n)** where `n` is the length of the string.

## **Space Complexity**
- **O(k)** where `k` is the number of unique characters (bounded by the character set, e.g., 26 or 128).

---

## **Code**

```java
class Solution {
    public static int lengthOfLongestSubstring(String s) {
        Set<Character> seen = new HashSet<>();
        int left = 0, maxLength = 0;

        for (int right = 0; right < s.length(); right++) {
            char currentChar = s.charAt(right);

            while (seen.contains(currentChar)) {
                seen.remove(s.charAt(left));
                left++;
            }

            seen.add(currentChar);
            maxLength = Math.max(maxLength, right - left + 1);
        }

        return maxLength;
    }
}
```
