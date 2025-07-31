# Explanation: Merge Two Sorted Lists

**Problem:** [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists)

**Difficulty:** Easy

---

## Description

You are given the heads of two **sorted** linked lists `list1` and `list2`.

Merge the two lists into **one sorted linked list** and return the head of the merged list.

The merged list should be made by splicing together the nodes of the first two lists.

---

## Examples

**Example 1**  
**Input:** `list1 = [1,2,4]`, `list2 = [1,3,4]`  
**Output:** `[1,1,2,3,4,4]`

**Example 2**  
**Input:** `list1 = []`, `list2 = []`  
**Output:** `[]`

**Example 3**  
**Input:** `list1 = []`, `list2 = [0]`  
**Output:** `[0]`

---

## Approach

We use a **dummy head node** to simplify pointer manipulation.

1. Create a dummy node and a pointer `current` pointing to it.
2. Traverse both lists:
   - Compare the current nodes of both lists.
   - Append the smaller node to the merged list.
   - Advance the pointer in the selected list.
3. After the loop, if one list still has nodes left, append the remainder.
4. Return `dummy.next` which is the head of the merged list.

---

## Time and Space Complexity

- **Time Complexity:** O(n + m) – where `n` and `m` are the lengths of the input lists.
- **Space Complexity:** O(1) – only pointers are used; we reuse existing nodes.

---

## Code (Java)

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
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        ListNode dummy = new ListNode(0);
        ListNode current = dummy;

        while (list1 != null && list2 != null) {
            if (list1.val < list2.val) {
                current.next = list1;
                list1 = list1.next;
            } else {
                current.next = list2;
                list2 = list2.next;
            }
            current = current.next;
        }

        if (list1 != null) {
            current.next = list1;
        } else {
            current.next = list2;
        }

        return dummy.next;
    }
}
