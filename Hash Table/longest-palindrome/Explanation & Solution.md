# **Explanation: Longest Palindrome**

## **Problem:** [Longest Palindrome – LeetCode](https://leetcode.com/problems/longest-palindrome/)

**Difficulty:** Easy  
**Topic:** String, HashMap

---

## **Description**  
Given a string `s`, find the length of the **longest palindrome** that can be built with those letters.

Letters are case-sensitive (e.g., `"Aa"` is not considered a palindrome here).

---

## **Examples**

**Example 1**  
**Input:** `s = "abccccdd"`  
**Output:** `7`  
**Explanation:** One longest palindrome that can be built is `"dccaccd"` which has length 7.

---

## **Approach**

We count the occurrences of each character using a `HashMap`. A palindrome can be formed by pairing characters, and potentially placing a single unmatched character in the center.

1. Create a `HashMap<Character, Integer>` to count occurrences of each character in `s`.
2. Traverse the counts:
   - If the count is even → add the full count.
   - If it's odd → add (count - 1) and set a flag `flag = true`.
3. After summing, if there was at least one odd count (`flag == true`), we can add `1` to place one character in the middle.
4. Return the total length `cnt`.

---

## **Time and Space Complexity**

- **Time Complexity:** O(n) — one pass to count characters, one pass to sum.
- **Space Complexity:** O(1) — since the `HashMap` has at most a fixed number of entries (assuming ASCII character set).

---

## **Code (Java)**

```java
class Solution {
    public int longestPalindrome(String s) {
        HashMap<Character, Integer> hash = new HashMap<>();
        for (int i = 0; i < s.length(); i++) {
            char c = s.charAt(i);
            hash.put(c, hash.getOrDefault(c, 0) + 1);
        }

        int cnt = 0;
        boolean flag = false;

        for (int value : hash.values()) {
            if (value % 2 == 0) {
                cnt += value;
            } else {
                flag = true;
                cnt += value - 1;
            }
        }

        if (flag) {
            cnt += 1;
        }

        return cnt;
    }
}
