# **Explanation: Search Insert Position**

## **Problem:** [Search Insert Position – LeetCode](https://leetcode.com/problems/search-insert-position/)

### **Difficulty Level:** Easy

---

## **Description**  
Given a **sorted array** of distinct integers and a target value, return the **index if the target is found**.  
If not, return the **index where it would be if it were inserted in order**.

You must write an algorithm with **O(log n)** runtime complexity.

---

## **Examples**

**Example 1**  
**Input:** `nums = [1,3,5,6]`, `target = 5`  
**Output:** `2`

**Example 2**  
**Input:** `nums = [1,3,5,6]`, `target = 2`  
**Output:** `1`

**Example 3**  
**Input:** `nums = [1,3,5,6]`, `target = 7`  
**Output:** `4`

---

## **Approach**

We use **binary search**:

- Start with `left = 0` and `right = nums.length - 1`.
- While `left <= right`, compute `mid`.
- If `nums[mid] == target`, return `mid`.
- If `nums[mid] > target`, move `right = mid - 1`.
- If `nums[mid] < target`, move `left = mid + 1`.

After the loop, `left` will be the correct insertion position.

---

## **Time Complexity:**  
- **O(log n)** – Classic binary search.

## **Space Complexity:**  
- **O(1)** – No additional space used.

---

## **Code (Java)**

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int left = 0, right = nums.length - 1;

        while (left <= right) {
            int mid = left + (right - left) / 2;

            if (nums[mid] == target)
                return mid;
            else if (nums[mid] > target)
                right = mid - 1;
            else
                left = mid + 1;
        }

        return left;
    }
}
