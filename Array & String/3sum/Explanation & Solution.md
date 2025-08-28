# **Explanation: 3Sum**


## **Problem:** [3Sum – LeetCode](https://leetcode.com/problems/3sum/)

**Difficulty:** Medium  
**Topic:** Array, Two Pointers, Sorting

---

## **Description**  
Given an integer array `nums`, return all unique triplets `[nums[i], nums[j], nums[k]]` such that:
- `i`, `j`, and `k` are different indices,
- and `nums[i] + nums[j] + nums[k] == 0`.

The result set must not contain duplicate triplets (regardless of order).

---

## **Examples**

**Example 1**  
**Input:** `nums = [-1,0,1,2,-1,-4]`  
**Output:** `[[-1,-1,2],[-1,0,1]]`

**Example 2**  
**Input:** `nums = []`  
**Output:** `[]`

**Example 3**  
**Input:** `nums = [0]`  
**Output:** `[]`

---

## **Approach**

###  Optimal Solution – Sort + Two Pointers

1. **Sort** the array.
2. Iterate through each index `i` from `0` to `nums.length - 3`:
   - Skip duplicate values: if `i > 0 && nums[i] == nums[i - 1]` → continue.
3. Use two pointers: `left = i + 1`, `right = nums.length - 1`.
4. While `left < right`:
   - Compute `sum = nums[i] + nums[left] + nums[right]`.
   - If `sum < 0` → `left++` (need larger value).
   - If `sum > 0` → `right--` (need smaller value).
   - If `sum == 0`:
     - Found valid triplet → add `[nums[i], nums[left], nums[right]]` to result.
     - Increment `left` and decrement `right`.
     - Skip duplicate values: while `left < right && nums[left] == nums[left - 1]`, `left++`.

This yields **O(n²)** time and **O(log n)** space (for sorting), or **O(1)** extra space if sort is in-place.

---

## **Time & Space Complexity**

- **Time Complexity:** `O(n²)` — sorting + nested two pointers loop.
- **Space Complexity:** `O(log n)` for sort stack (or `O(1)` auxiliary).

---

## **Code (Java)**

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> result = new ArrayList<>();
        Arrays.sort(nums);

        for (int i = 0; i < nums.length - 2; i++) {
            if (i > 0 && nums[i] == nums[i - 1]) continue; // skip duplicates

            int left = i + 1, right = nums.length - 1;
            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];

                if (sum < 0) {
                    left++;
                } else if (sum > 0) {
                    right--;
                } else {
                    result.add(Arrays.asList(nums[i], nums[left], nums[right]));
                    left++;
                    right--;

                    // skip duplicates
                    while (left < right && nums[left] == nums[left - 1]) left++;
                    while (left < right && nums[right] == nums[right + 1]) right--;
                }
            }
        }
        return result;
    }
}
