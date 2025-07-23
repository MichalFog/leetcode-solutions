# **Explanation: Add Two Numbers**

## **Problem:** [Add Two Numbers - LeetCode](https://leetcode.com/problems/add-two-numbers/)

### **Difficulty Level:** Medium

---

## **Description**  
You are given two **non-empty** linked lists representing two non-negative integers.  
The digits are stored in **reverse order**, and each of their nodes contains a single digit.  
Add the two numbers and return the sum as a linked list.

- You may assume the two numbers do not contain any leading zero, except the number 0 itself.

---

## **Example**

**Input:**  
l1 = [2,4,3]
l2 = [5,6,4]

makefile
Copy
Edit
**Output:**  
[7,0,8]

yaml
Copy
Edit
**Explanation:**  
342 + 465 = 807 → reversed list: [7,0,8]

---

**Input:**  
l1 = [0]
l2 = [0]

makefile
Copy
Edit
**Output:**  
[0]

css
Copy
Edit

**Input:**  
l1 = [9,9,9,9,9,9,9]
l2 = [9,9,9,9]

makefile
Copy
Edit
**Output:**  
[8,9,9,9,0,0,0,1]

yaml
Copy
Edit

---

## **Approach**

We simulate the addition manually, digit by digit, using a dummy node and a `carry`:

1. Initialize:
   - A dummy head for the result list.
   - A pointer `dummy` to build the result list.
   - `carry = 0`.

2. While either `l1`, `l2`, or `carry` exists:
   - Add the values from `l1` and `l2` (if available) and the `carry`.
   - Create a new node with value `total % 10`.
   - Update `carry = total / 10`.

3. Return `dummyHead.next` (skip the dummy node).

This method efficiently builds the result while traversing both lists only once.

---

## **Time Complexity**
- **O(max(n, m))**, where `n` and `m` are the lengths of `l1` and `l2`.

## **Space Complexity**
- **O(max(n, m))** for the new linked list.

---

## **Code**

```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode();
        ListNode res = dummy;
        int total = 0, carry = 0;

        while (l1 != null || l2 != null || carry != 0) {
            total = carry;

            if (l1 != null) {
                total += l1.val;
                l1 = l1.next;
            }
            if (l2 != null) {
                total += l2.val;
                l2 = l2.next;
            }

            int num = total % 10;
            carry = total / 10;
            dummy.next = new ListNode(num);
            dummy = dummy.next;
        }

        return res.next;        
    }
}
