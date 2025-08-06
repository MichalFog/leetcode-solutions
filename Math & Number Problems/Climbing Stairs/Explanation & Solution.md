# **Explanation: Climbing Stairs**

## **Problem:** [Climbing Stairs – LeetCode](https://leetcode.com/problems/climbing-stairs/)

### **Difficulty Level:** Easy

---

## **Description**  
You are climbing a staircase. It takes `n` steps to reach the top.  
Each time you can either climb **1** or **2** steps.  
In how many distinct ways can you climb to the top?

---

## **Examples**

**Example 1**  
**Input:** `n = 2`  
**Output:** `2`  
**Explanation:** 1 step + 1 step OR 2 steps

**Example 2**  
**Input:** `n = 3`  
**Output:** `3`  
**Explanation:**  
- 1 step + 1 step + 1 step  
- 1 step + 2 steps  
- 2 steps + 1 step

---

## **Approach**

This problem follows the Fibonacci pattern:

- If `n = 1`, there is only 1 way to climb (1 step).  
- If `n = 2`, there are 2 ways (1+1 or 2).  
- For `n >= 3`, the number of ways to climb is the sum of the ways to climb `n-1` and `n-2` steps.

We use iteration to avoid recursion and stack overflow for large `n`.

### **Steps**:

1. Handle base cases (`n = 1` or `n = 2`).
2. Use two variables to store the number of ways to reach the previous two steps.
3. Iterate from 3 to `n`, updating the total number of ways.

---

## **Time and Space Complexity**

- **Time Complexity:** `O(n)` — we iterate once from 3 to `n`.
- **Space Complexity:** `O(1)` — only a few variables are used.

---

## **Code (Java)**

```java
class Solution {
    public int climbStairs(int n) {
        if (n <= 2) return n;

        int oneStepBefore = 2; 
        int twoStepsBefore = 1; 
        int allWays = 0;

        for (int i = 3; i <= n; i++) {
            allWays = oneStepBefore + twoStepsBefore;
            twoStepsBefore = oneStepBefore;
            oneStepBefore = allWays;
        }

        return allWays;
    }
}
