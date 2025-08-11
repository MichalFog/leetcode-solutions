# **Explanation: Single Number**

## **Problem:** [Single Number – LeetCode](https://leetcode.com/problems/single-number/)

### **Difficulty:** Easy

---

## **Description**  
Given a **non-empty** array of integers `nums`, every element appears **twice** except for one. Find that single one.

---

## **Examples**

**Example 1**  
**Input:** `nums = [2,2,1]`  
**Output:** `1`

**Example 2**  
**Input:** `nums = [4,1,2,1,2]`  
**Output:** `4`

**Example 3**  
**Input:** `nums = [1]`  
**Output:** `1`

---

## **Approach**

### **Idea:**  
We use a **HashMap** to count how many times each number appears.  
The number that appears exactly once is the answer.

---

## **Steps**:
1. Create a `HashMap<Integer, Integer>` to store the frequency of each number.
2. Loop over the array:
   - Increment the count for each number.
3. Loop again over the array:
   - Return the number with a frequency of `1`.
4. If none found (shouldn't happen per problem constraints) → return `-1`.

---

## **Time and Space Complexity**

- **Time Complexity:** `O(n)` — we loop through the array twice.  
- **Space Complexity:** `O(n)` — we store counts in the map.

---

## **Code (Java)**

```java
import java.util.HashMap;

public class Solution {
    public int singleNumber(int[] nums) {
        HashMap<Integer, Integer> map = new HashMap<>();
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

        for (int num : nums) {
            if (map.get(num) == 1) {
                return num;
            }
        }

        return -1; 
    }
}
