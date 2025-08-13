# **Explanation: Find Peak Element**

## **Problem:** [Find Peak Element – LeetCode](https://leetcode.com/problems/find-peak-element/)

### **Difficulty:** Medium

---

## **Description**  
A peak element is an element that is strictly greater than its neighbors.  
Given an integer array `nums`, find a peak element and return its index.  
If the array contains multiple peaks, return the index of any of them.  

You may imagine that `nums[-1] = -∞` and `nums[n] = -∞`.

---

## **Examples**

**Example 1**  
**Input:**  
nums = [1,2,3,1]

makefile
Copy
Edit
**Output:**  
2

Explanation: `nums[2] = 3` is a peak.

---

**Example 2**  
**Input:**  
nums = [1,2,1,3,5,6,4]

makefile
**Output:**  
1 or 5

Explanation: Both `nums[1] = 2` and `nums[5] = 6` are peaks.

---

## **Approach**

### **Idea:**  
We can use **Binary Search** to find a peak in `O(log n)` time:
- If `nums[mid] < nums[mid + 1]` → peak must be on the **right side**.
- Else → peak must be on the **left side** (including `mid`).

The process continues until `left == right`, which will be the index of a peak.

---

## **Steps**:
1. Set `left = 0`, `right = nums.length - 1`.
2. While `left < right`:
   - Find `mid = left + (right - left) / 2`.
   - If `nums[mid] < nums[mid + 1]` → `left = mid + 1`.
   - Else → `right = mid`.
3. Return `right` (or `left`, they will be equal).

---

## **Time and Space Complexity**

- **Time Complexity:** `O(log n)` — binary search.
- **Space Complexity:** `O(1)` — constant extra space.

---

## **Code (Java)**

```java
class Solution {
    public int findPeakElement(int[] nums) {
        int left = 0, right = nums.length - 1;

        while (left < right) {
            int mid = left + (right - left) / 2;
            if (nums[mid] < nums[mid + 1]) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        return right;
    }
}
