# **Explanation: Median of Two Sorted Arrays**

## **Problem:** [Median of Two Sorted Arrays - LeetCode](https://leetcode.com/problems/median-of-two-sorted-arrays/)

### **Difficulty Level:** Hard

---

## **Description**  
You are given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively.  
Return the median of the two sorted arrays.  
The overall run time complexity should be **O(log (m+n))**.

---

## **Example**

**Input:** `nums1 = [1,3]`, `nums2 = [2]`  
**Output:** `2.0`  
**Explanation:** The merged array is `[1,2,3]`, and the median is `2`.

**Input:** `nums1 = [1,2]`, `nums2 = [3,4]`  
**Output:** `2.5`  
**Explanation:** The merged array is `[1,2,3,4]`, and the median is `(2 + 3) / 2 = 2.5`.

---

## **Approach**

This is a classic **divide and conquer** problem solved using **binary search**.

### Key ideas:
- Ensure `nums1` is the smaller array (for binary search efficiency).
- We perform a binary search on `nums1` to find the correct partition.
- The goal is to find a partition such that:
  - the left part of both arrays combined contains exactly half of the total elements.
  - every element on the left side is less than or equal to every element on the right side.

### Steps:
1. Binary search on the smaller array.
2. At each step, partition `nums1` and `nums2` such that the left half contains the correct number of elements.
3. Check if max of left ≤ min of right on both sides.
4. If valid partition found:
   - If total length is even → return average of max of left and min of right.
   - If odd → return max of left.
5. Adjust binary search range if not valid.

This approach guarantees **O(log(min(m,n)))** time complexity.

---

## **Time Complexity**
- **O(log(min(m, n)))** where `m` and `n` are the lengths of `nums1` and `nums2`.

## **Space Complexity**
- **O(1)** — we use constant space.

---

## **Code (Java)**

```java
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        if (nums1.length > nums2.length)
            return findMedianSortedArrays(nums2, nums1); // ensure nums1 is smaller

        int x = nums1.length;
        int y = nums2.length;
        int low = 0, high = x;

        while (low <= high) {
            int partitionX = (low + high) / 2;
            int partitionY = (x + y + 1) / 2 - partitionX;

            int maxLeftX = (partitionX == 0) ? Integer.MIN_VALUE : nums1[partitionX - 1];
            int minRightX = (partitionX == x) ? Integer.MAX_VALUE : nums1[partitionX];

            int maxLeftY = (partitionY == 0) ? Integer.MIN_VALUE : nums2[partitionY - 1];
            int minRightY = (partitionY == y) ? Integer.MAX_VALUE : nums2[partitionY];

            if (maxLeftX <= minRightY && maxLeftY <= minRightX) {
                if ((x + y) % 2 == 0)
                    return ((double)Math.max(maxLeftX, maxLeftY) + Math.min(minRightX, minRightY)) / 2;
                else
                    return (double)Math.max(maxLeftX, maxLeftY);
            } else if (maxLeftX > minRightY) {
                high = partitionX - 1;
            } else {
                low = partitionX + 1;
            }
        }

        throw new IllegalArgumentException("Input arrays are not sorted properly.");
    }
}
