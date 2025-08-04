# **Explanation: Plus One**

## **Problem:** [Plus One – LeetCode](https://leetcode.com/problems/plus-one/)

### **Difficulty Level:** Easy

---

## **Description**  
You are given a **large integer** represented as an integer array `digits`, where each `digits[i]` is the i-th digit of the integer.

The digits are ordered from **most significant to least significant** in left to right order.

Increment the large integer by one and return the resulting array of digits.

---

## **Examples**

**Example 1**  
**Input:** `digits = [1,2,3]`  
**Output:** `[1,2,4]`  
**Explanation:** The array represents the number `123`. Adding one gives `124`.

**Example 2**  
**Input:** `digits = [4,3,2,1]`  
**Output:** `[4,3,2,2]`  
**Explanation:** The array represents the number `4321`. Adding one gives `4322`.

**Example 3**  
**Input:** `digits = [9,9,9]`  
**Output:** `[1,0,0,0]`  
**Explanation:** The array represents `999`. Adding one causes a carry across all digits.

---

## **Approach**

We iterate **backwards** from the end of the array:

1. Increment the current digit.
2. If the result is less than 10, return the array.
3. If the digit becomes 10, set it to `0` and continue to propagate the carry.

If we finish the loop and all digits were `9`, we create a **new array** of length `n+1` with `1` at the beginning (e.g., `999 + 1 = 1000`).

---

## **Time Complexity:**  
- **O(n)** – We may need to visit every digit.

## **Space Complexity:**  
- **O(n)** – In the worst case, we create a new array of size `n + 1`.

---

## **Code (Java)**

```java
class Solution {
    public int[] plusOne(int[] digits) {
        for (int i = digits.length - 1; i >= 0; i--) {
            digits[i]++;
            if (digits[i] < 10) {
                return digits;
            }
            digits[i] = 0;
        }

        int[] result = new int[digits.length + 1];
        result[0] = 1;  
        return result;
    }
}
