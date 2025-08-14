# **Explanation: Majority Element**

## **Problem:** [Majority Element – LeetCode](https://leetcode.com/problems/majority-element/)

**Difficulty:** Easy

---

## **Description**  
Given an array of size `n`, find the element that appears more than ⌊n/2⌋ times. You may assume that the majority element always exists in the array.

---

## **Examples**

**Example 1**  
**Input:** `nums = [3,2,3]`  
**Output:** `3`

**Example 2**  
**Input:** `nums = [2,2,1,1,1,2,2]`  
**Output:** `2`

---

## **Approach**

### ​ Optimal (Boyer–Moore Voting Algorithm)

We use two variables:
- `count` – tracks current vote balance
- `candidate` – potential majority element

Algorithm:
1. Initialize `count = 0`, `candidate = 0`.
2. For each number in `nums`:
   - If `count == 0`, set `candidate = num`.
   - If `num == candidate`, `count++`, else `count--`.
3. After one pass, the `candidate` is guaranteed to be the majority element.

This works because the majority element, appearing more than half the time, cannot be fully canceled out by other elements.

---

## **Time and Space Complexity**

- **Time Complexity:** `O(n)` — single pass through the array.
- **Space Complexity:** `O(1)` — uses only constant extra space.

---

## **Code (Java)**

```java
class Solution {
    public int majorityElement(int[] nums) {
        int count = 0;
        int candidate = 0;

        for (int num : nums) {
            if (count == 0) {
                candidate = num;
            }

            if (num == candidate) {
                count++;
            } else {
                count--;
            }
        }

        return candidate;
    }
}
