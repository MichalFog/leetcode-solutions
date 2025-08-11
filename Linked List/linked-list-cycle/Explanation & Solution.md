# **Explanation: Linked List Cycle**

## **Problem:** [Linked List Cycle – LeetCode](https://leetcode.com/problems/linked-list-cycle/)

### **Difficulty:** Easy

---

## **Description**  
Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

A linked list has a cycle if there is a node in the list that can be reached again by continuously following the `next` pointer.

---

## **Examples**

**Example 1**  
**Input:** `head = [3,2,0,-4], pos = 1`  
**Output:** `true`  
**Explanation:** There is a cycle linking the tail node to the node at index 1.

**Example 2**  
**Input:** `head = [1,2], pos = 0`  
**Output:** `true`

**Example 3**  
**Input:** `head = [1], pos = -1`  
**Output:** `false`

---

## **Approach**

### **Idea:**  
Use **Floyd’s Cycle Detection Algorithm** (also known as the "Tortoise and Hare" method):  
- Use two pointers, `slow` and `fast`.  
- `slow` moves one step at a time, `fast` moves two steps.  
- If the linked list contains a cycle, `fast` and `slow` will eventually meet inside the cycle.  
- If there is no cycle, `fast` will reach `null`.

---

## **Steps**:
1. If the list is empty or has only one node → no cycle (`false`).
2. Initialize:
   - `slow = head`
   - `fast = head`
3. Move:
   - `slow` by 1 node
   - `fast` by 2 nodes
4. If `slow == fast` → cycle detected (`true`).
5. If `fast` or `fast.next` becomes `null` → no cycle (`false`).

---

## **Time and Space Complexity**

- **Time Complexity:** `O(n)` — each pointer moves through the list at most once.  
- **Space Complexity:** `O(1)` — no extra data structure is used.

---

## **Code (Java)**

```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public boolean hasCycle(ListNode head) {
        if (head == null || head.next == null) return false;

        ListNode slow = head;
        ListNode fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;       
            fast = fast.next.next;    

            if (slow == fast) return true; 
        }

        return false; 
    }
}
