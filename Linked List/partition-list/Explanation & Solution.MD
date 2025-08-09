# **Explanation: Partition List**

## **Problem:** [Partition List – LeetCode](https://leetcode.com/problems/partition-list/)

### **Difficulty Level:** Medium

---

## **Description**  
Given the `head` of a linked list and an integer `x`, partition it such that:  
- All nodes with values **less than `x`** come before nodes **greater than or equal to `x`**.  
- The relative order of nodes in each partition is preserved.

---

## **Examples**

**Example 1**  
**Input:** `head = [1,4,3,2,5,2]`, `x = 3`  
**Output:** `[1,2,2,4,3,5]`

**Example 2**  
**Input:** `head = [2,1]`, `x = 2`  
**Output:** `[1,2]`

---

## **Approach**

### **Idea:**  
We create **two separate linked lists**:
- `small` for nodes with value < `x`
- `big` for nodes with value ≥ `x`

We iterate through the original list and:
1. Append nodes with value < `x` to `small`.
2. Append nodes with value ≥ `x` to `big`.
3. At the end, connect the `small` list to the `big` list.

This ensures both:
- Partitioning is correct.
- Original relative order is preserved.

---

## **Steps**:

1. Create two dummy nodes: `small` and `big` to represent the two lists.
2. Keep two pointers (`temp1` for `small`, `temp2` for `big`) to track their heads.
3. Traverse the original list:
   - If the value is < `x`, append to `small` and move the pointer.
   - Else, append to `big` and move the pointer.
4. Connect the `small` list to the `big` list.
5. Return the head of the `small` list (skipping the dummy).

---

## **Time and Space Complexity**

- **Time Complexity:** `O(n)` — visiting each node once.
- **Space Complexity:** `O(n)` — creating new nodes for the partitioned lists.

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
    public ListNode partition(ListNode head, int x) {
        ListNode big = new ListNode(0);
        ListNode small = new ListNode(0);
        ListNode temp1 = small; 
        ListNode temp2 = big; 

        while (head != null) {
            if (head.val < x) {
                small.next = new ListNode(head.val);
                small = small.next;
            } else {
                big.next = new ListNode(head.val);
                big = big.next;
            }
            head = head.next;
        }

        small.next = temp2.next; // connect small list to big list
        return temp1.next;
    }
}
