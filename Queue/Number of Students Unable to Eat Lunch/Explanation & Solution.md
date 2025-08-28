# **Explanation: Number of Students Unable to Eat Lunch**


## **Problem:** [Number of Students Unable to Eat Lunch – LeetCode](https://leetcode.com/problems/number-of-students-unable-to-eat-lunch/)

**Difficulty:** Medium  
**Topic:** Array, Counting, Simulation

---

## **Description**  
There is a queue of students and a stack of sandwiches. Students are in the order given by `students[]` where:
- `0` indicates a student who prefers circular sandwiches.
- `1` indicates a student preferring square sandwiches.

The sandwiches stack is given by `sandwiches[]` where the first element is the top.  
At each step:
1. If the student at the front of the queue prefers the sandwich on top, they take it and leave the queue.
2. Otherwise, the student moves to the back of the queue.
The process continues until no student in the queue wants the top sandwich.

Return **the number of students who are unable to eat**.

---

## **Examples**

**Example 1**  
**Input:**  
```text
students = [1,1,0,0],  
sandwiches = [0,1,0,1]
```
**Output:** `0`  
**Explanation:** All students can eat in this order.

**Example 2**  
**Input:**  
```text
students = [1,1,1,0,0,1],  
sandwiches = [1,0,0,0,1,1]
```
**Output:** `3`  
**Explanation:** Three students cannot find a sandwich matching their preference at the end.

---

## **Optimal Approach (Counting Only)**

Instead of simulating the queue, we can use a counting strategy:

1. Count how many students prefer each type:
   - `count[0]` for circular-preferring students
   - `count[1]` for square-preferring students
2. Iterate through the sandwiches stack:
   - If no student prefers the top sandwich (`count[sandwich] == 0`), stop and return the number of students left, which is `count[1 - sandwich]`.
   - Otherwise, decrement `count[sandwich]` as one student takes it.
3. If all sandwiches are successfully taken, return `0`.

This method achieves **O(n)** time and **O(1)** space complexity.

---

## **Complexity**

- **Time Complexity:** `O(n)` — single pass through the sandwiches.
- **Space Complexity:** `O(1)` — constant extra space for counting.

---

## **Code (Java)**

```java
class Solution {
    public int countStudents(int[] students, int[] sandwiches) {
        int[] count = new int[2];
        for (int stu : students) {
            count[stu]++;
        }

        for (int sandwich : sandwiches) {
            if (count[sandwich] == 0) {
                // No more students prefer this sandwich → stop
                return count[sandwich ^ 1];
            }
            count[sandwich]--;
        }

        // All students served
        return 0;
    }
}
```

---

## **Why It Works**

Once the top sandwich doesn't match any student preference, further processing cannot change this. Therefore, the remaining unmatched students are simply those who prefer the other sandwich type. This removes the need to simulate the queue behavior, simplifying the solution while staying optimal.

---

## **Video Explanation**  
[Number of Students Unable to Eat Lunch – LeetCode| Array, Queue, Simulation](https://www.youtube.com/watch?v=aSNb6BSw0p0&utm_source=chatgpt.com)
