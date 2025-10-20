
# **Explanation: Intersection of Two Linked Lists**

## **Problem:** [Intersection of Two Linked Lists – LeetCode](https://leetcode.com/problems/intersection-of-two-linked-lists/)

### **Difficulty:** Easy

---

## **Description**  
Given the heads of two singly linked lists `headA` and `headB`, return the node at which the two lists intersect.  
If the two linked lists have no intersection, return `null`.

---

## **Examples**

**Example 1**  
**Input:**  
A = [4,1,8,4,5]
B = [5,6,1,8,4,5]
intersect at 8

markdown
**Output:** Node with value 8

**Example 2**  
**Input:**  
A = [1,9,1,2,4]
B = [3,2,4]
intersect at 2

markdown
**Output:** Node with value 2

**Example 3**  
**Input:**  
A = [2,6,4]
B = [1,5]
no intersection

**Output:** null

---

## **Approach**

### **Idea:**  
We use **two pointers**:
- Pointer `a` starts at `headA`
- Pointer `b` starts at `headB`
- When a pointer reaches the end of its list, it jumps to the head of the other list.
- If the lists intersect, both pointers will eventually meet at the intersection node.  
- If they do not intersect, both will reach `null` at the same time.

---

## **Steps**:
1. Initialize `a = headA`, `b = headB`.
2. While `a != b`:
   - If `a` reaches end → move it to `headB`.
   - If `b` reaches end → move it to `headA`.
   - Otherwise, move each one step forward.
3. When `a == b`, return that node (or `null` if no intersection).

---

## **Time and Space Complexity**

- **Time Complexity:** `O(m + n)` — where `m` and `n` are lengths of the two lists.  
- **Space Complexity:** `O(1)` — no extra storage.

---

## **Code (Java)**

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if (headA == null || headB == null) return null;

        ListNode a = headA;
        ListNode b = headB;

        while (a != b) {
            a = (a == null) ? headB : a.next;
            b = (b == null) ? headA : b.next;
        }

        return a; 
    }
}
