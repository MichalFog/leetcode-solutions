# **Explanation: Remove Duplicates from Sorted List**

## **Problem:** [Remove Duplicates from Sorted List – LeetCode](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

### **Difficulty Level:** Easy

---

## **Description**  
Given the `head` of a **sorted** linked list, delete all duplicates such that each element appears only once.  
Return the linked list **sorted** as well.

---

## **Examples**

**Example 1**  
**Input:** `head = [1,1,2]`  
**Output:** `[1,2]`

**Example 2**  
**Input:** `head = [1,1,2,3,3]`  
**Output:** `[1,2,3]`

---

## **Approach**

### **Idea:**  
We traverse the linked list while keeping track of values we have already seen using a **HashSet**:

1. If the next node's value already exists in the set, we **skip** it by adjusting the `next` pointer.
2. If it doesn't exist, we add it to the set and move forward.
3. Continue until we reach the end of the list.

---

## **Steps**:

1. Handle the edge case where the list is empty (`head == null`).
2. Initialize a `HashSet<Integer>` to store seen values.
3. Iterate over the list:
   - If `current.next` has a duplicate value, skip it (`current.next = current.next.next`).
   - Else, add the value to the set and move to the next node.
4. Return the head.

---

## **Time and Space Complexity**

- **Time Complexity:** `O(n)` — each node is visited once.
- **Space Complexity:** `O(n)` — storing unique values in a set.

---

## **Code (Java)**

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        if (head == null)
            return head;

        HashSet<Integer> hash = new HashSet<>();
        ListNode current = head;
        hash.add(current.val);

        while (current.next != null) {
            if (hash.contains(current.next.val)) {
                current.next = current.next.next;
            } else {
                hash.add(current.next.val);
                current = current.next;
            }
        }

        return head;
    }
}
