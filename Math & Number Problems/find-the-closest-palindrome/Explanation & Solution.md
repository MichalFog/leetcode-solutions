# **Explanation: Find the Closest Palindrome**

## **Problem:**
[Find the Closest Palindrome – LeetCode](https://leetcode.com/problems/find-the-closest-palindrome/)

**Difficulty:** Hard  
**Topic:** Math, String, Palindrome

---

## **Description**  
Given a string `n` representing a positive integer, return the **closest palindrome** (as a string) that is **not** equal to `n`.  
If there is a tie (two palindromes equally close), return the **smaller** one.

---

## **Examples**

```text
Input: "123"
Output: "121"

Input: "1"
Output: "0"

Explanation: Both 0 and 2 are equally close, so return the smaller one: "0".
Optimal Approach: Prefix Mirror + Candidates

Instead of brute forcing all numbers around n, build a small set of palindromic candidates based on n:

Edge palindromes:

10^len + 1 — e.g., adjacent palindrome above length.

10^(len-1) - 1 — e.g., all 9’s below length.

Mirror the prefix:

Let prefix = n[:(len+1)//2].

For each i in {prefix-1, prefix, prefix+1}:

Create a palindrome by mirroring i (excluding middle digit if needed).

Remove n itself from candidates (if it is a palindrome).

Pick the closest:

Compare by absolute difference to n.

In a tie, choose numerically smaller.

Typically, this approach inspects at most 5 candidates and runs in O(d) where d is number of digits (up to 18).

Time & Space Complexity

Time Complexity: O(d) – generating limited candidates and comparing them.

Space Complexity: O(d) – for strings and candidate set.

Code (Java)
class Solution {
    public String nearestPalindromic(String n) {
        int len = n.length();
        long original = Long.parseLong(n);
        Set<Long> candidates = new HashSet<>();

        candidates.add((long) Math.pow(10, len - 1) - 1);
        candidates.add((long) Math.pow(10, len) + 1);

        long prefix = Long.parseLong(n.substring(0, (len + 1) / 2));
        for (long x = prefix - 1; x <= prefix + 1; x++) {
            String s = String.valueOf(x);
            String rev = new StringBuilder(s).reverse().toString();
            String palin = (len % 2 == 0) ? s + rev : s + rev.substring(1);
            candidates.add(Long.parseLong(palin));
        }

        candidates.remove(original);

        long closest = -1;
        for (long cand : candidates) {
            if (cand < 0) continue;
            long diff = Math.abs(cand - original);
            if (closest == -1 || diff < Math.abs(closest - original) ||
               (diff == Math.abs(closest - original) && cand < closest)) {
                closest = cand;
            }
        }

        return String.valueOf(closest);
    }
}
