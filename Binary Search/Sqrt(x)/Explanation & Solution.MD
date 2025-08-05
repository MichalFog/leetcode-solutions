# **Explanation: Sqrt(x)**

## **Problem:** [Sqrt(x) – LeetCode](https://leetcode.com/problems/sqrtx/)

### **Difficulty Level:** Easy

---

## **Description**  
Given a non-negative integer `x`, return the **square root of `x` rounded down to the nearest integer**.  
The returned integer should be the **floor** of `√x`.

You must not use any built-in exponent function or operator such as `pow(x, 0.5)` or `x ** 0.5`.

---

## **Examples**

**Example 1**  
**Input:** `x = 4`  
**Output:** `2`  
**Explanation:** `√4 = 2`, so return 2.

**Example 2**  
**Input:** `x = 8`  
**Output:** `2`  
**Explanation:** `√8 ≈ 2.8284`, so return floor of it which is `2`.

---

## **Approach**

### 🔍 Binary Search

1. Handle base cases: If `x < 2`, return `x`.
2. Initialize binary search range from `1` to `x/2`.
3. For each `mid`, compute `mid * mid` using `long` to avoid overflow.
4. If `mid² == x`, return `mid`.
5. If `mid² < x`, move to the right half.
6. If `mid² > x`, move to the left half.
7. If no exact match found, return `right`, which will point to the floor of the square root.

---

## **Time Complexity:**  
- **O(log x)** – Binary search over the range `1` to `x/2`.

## **Space Complexity:**  
- **O(1)** – Constant extra space used.

---

## **Code (Java)**

```java
class Solution {
    public int mySqrt(int x) {
        if (x < 2) return x;

        int left = 1, right = x / 2;

        while (left <= right) {
            int mid = left + (right - left) / 2;
            long square = (long) mid * mid;

            if (square == x) {
                return mid;
            } else if (square < x) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return right;
    }
}
