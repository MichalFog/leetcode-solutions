# **Explanation: Find First and Last Position of Element in Sorted Array**

## **Problem:** [Find First and Last Position of Element in Sorted Array – LeetCode](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

### **Difficulty Level:** Medium

---

## **Description**  
Given an array of integers `nums` sorted in **non-decreasing order**, and a target value `target`, return the **starting and ending position** of `target` in `nums`.

If `target` is not found in the array, return `[-1, -1]`.

You must write an algorithm with **O(log n)** runtime complexity.

---

## **Examples**

**Example 1**  
**Input:** `nums = [5,7,7,8,8,10]`, `target = 8`  
**Output:** `[3,4]`

**Example 2**  
**Input:** `nums = [5,7,7,8,8,10]`, `target = 6`  
**Output:** `[-1,-1]`

**Example 3**  
**Input:** `nums = []`, `target = 0`  
**Output:** `[-1,-1]`

---

## **Approach**

We use **binary search** twice:

1. **First**, to find the **first occurrence** of the target.
2. **Second**, to find the **last occurrence** of the target.

Each search works in `O(log n)` time by narrowing the range:
- If the middle element equals the target, we continue searching either left (for first) or right (for last).
- If the middle is less than target, search right.
- If greater, search left.

---

## **Time Complexity:**  
- **O(log n)** – Two binary searches.

## **Space Complexity:**  
- **O(1)** – No extra space used.

---

## **Code (Java)**

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int first = findBound(nums, target, true);
        int last = findBound(nums, target, false);
        return new int[] { first, last };
    }

    private int findBound(int[] nums, int target, boolean isFirst) {
        int left = 0;
        int right = nums.length - 1;
        int result = -1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target) {
                result = mid;
                if (isFirst) {
                    right = mid - 1; 
                } else {
                    left = mid + 1; 
                }
            } else if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return result;
    }
}
