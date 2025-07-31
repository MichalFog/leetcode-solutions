# Explanation: Remove Duplicates from Sorted Array

**Problem:** [Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array)

**Difficulty:** Easy

---

## Description

Given an integer array `nums` sorted in **non-decreasing order**, remove the **duplicates in-place** such that each unique element appears only once.

Return the new length `k` of the array, and modify `nums` such that the first `k` elements contain the unique elements.

❗ You must **do this in-place** with **O(1)** extra memory.

---

## Examples

**Example 1**  
**Input:** `nums = [1,1,2]`  
**Output:** `k = 2, nums = [1,2,_]`  
**Explanation:** Your function should return `k = 2`, and the first two elements of `nums` should be `1` and `2`.

**Example 2**  
**Input:** `nums = [0,0,1,1,1,2,2,3,3,4]`  
**Output:** `k = 5, nums = [0,1,2,3,4,_,_,_,_,_]`  
**Explanation:** The unique elements should be moved to the beginning of the array.

---

## Approach

We use a **two-pointer technique**:

1. `k` points to the position where the next unique number should be placed.
2. Iterate through the array starting from index `1`.
3. For each element:
   - If it's **different from the previous** (`nums[i] != nums[i-1]`), it's unique.
   - Assign it to `nums[k]` and increment `k`.

Finally, return `k` as the count of unique elements.

---

## Time and Space Complexity

- **Time Complexity:** O(n) – we iterate through the array once.
- **Space Complexity:** O(1) – done in-place with constant extra space.

---

## Code (Java)

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int k = 1;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != nums[i - 1]) {
                nums[k] = nums[i];
                k++;
            }
        }
        return k;
    }
}
