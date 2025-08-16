# **Explanation: Rotate Array**

## **Problem:** [Rotate Array – LeetCode](https://leetcode.com/problems/rotate-array/)

**Difficulty:** Medium

---

## **Description**  
You are given an integer array `nums`, and an integer `k`. Rotate the array to the **right** by `k` steps, where `k` is non-negative.  
Elements shifted out of the end loop back to the front.

> **Example:** `nums = [1,2,3,4,5,6,7]`, `k = 3` → Result: `[5,6,7,1,2,3,4]`

---

## **Approach**

###  Optimal In-Place Solution: Reversal Algorithm

This method performs the rotation using **three reversals**, achieving **O(n)** time and **O(1)** extra space:

1. Compute `k = k % n` to handle cases where `k` exceeds array length.
2. **Reverse the entire array**.
3. **Reverse the first `k` elements**.
4. **Reverse the remaining `n - k` elements**.

This realigns the segments exactly as needed for a right rotation.

---

## **Steps**

1. Let `n = nums.length`.
2. Compute `k %= n`.
3. Reverse the subarray from index `0` to `n - 1`.
4. Reverse the subarray from `0` to `k - 1`.
5. Reverse the subarray from `k` to `n - 1`.
6. Done — `nums` is rotated in-place.

---

## **Time and Space Complexity**

- **Time Complexity:** O(n) — three full or partial reversals.
- **Space Complexity:** O(1) — only a few pointers used.

---

## **Code (Java)**

```java
class Solution {
    public void rotate(int[] nums, int k) {
        int n = nums.length;
        k %= n;

        reverse(nums, 0, n - 1);
        reverse(nums, 0, k - 1);
        reverse(nums, k, n - 1);
    }

    private void reverse(int[] nums, int start, int end) {
        while (start < end) {
            int tmp = nums[start];
            nums[start] = nums[end];
            nums[end] = tmp;
            start++;
            end--;
        }
    }
}
