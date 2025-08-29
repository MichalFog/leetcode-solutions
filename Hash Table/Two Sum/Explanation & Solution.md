# **Explanation & Solution: Two Sum**


## **Problem:** [Two Sum - LeetCode](https://leetcode.com/problems/two-sum)

### **Difficulty Level:** Easy

---

## **Description**  
Given an array of integers `nums` and an integer `target`, return **indices** of the two numbers such that they add up to `target`.  
You may assume that each input would have **exactly one solution**, and you **may not use the same element twice**.  
You can return the answer in **any order**.

---

## **Example**

**Input:** `nums = [2,7,11,15]`, `target = 9`  
**Output:** `[0,1]`  
**Explanation:**  
`nums[0] + nums[1] = 2 + 7 = 9`

**Input:** `nums = [3,2,4]`, `target = 6`  
**Output:** `[1,2]`  
**Explanation:**  
`nums[1] + nums[2] = 2 + 4 = 6`

**Input:** `nums = [3,3]`, `target = 6`  
**Output:** `[0,1]`

---

## **Approach**

We use a **HashMap** to store each number and its index as we iterate:

1. Loop through the array `nums`.
2. For each number, calculate its complement: `target - nums[i]`.
3. If the complement exists in the HashMap, return the indices.
4. If not, add the current number and its index to the HashMap.
5. Since the problem guarantees one solution, we return immediately when found.

This approach reduces the time complexity from O(n²) (brute force) to **O(n)**.

---

## **Time Complexity**
- **O(n)** where `n` is the number of elements in `nums`.

## **Space Complexity**
- **O(n)** for the HashMap.

---

## **Code**

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer,Integer> hash = new HashMap();
        for(int i = 0; i < nums.length; i++) {
            int num = target - nums[i];
            if(hash.containsKey(num)) {
                return new int[] { hash.get(num), i };
            }
            hash.put(nums[i], i);
        }
        return null;
    }
}
