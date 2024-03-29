# [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

## Solution

**Solution 1: Loop Traversals**

It adds two non-negative integers represented as linked lists digit by digit, using a dummy head node and tracking the current sum and carry values. The input lists are iterated simultaneously, and at each step, the sum is calculated, and a new node is created in the result linked list. The solution efficiently handles carry values and correctly generates the resulting linked list as the sum of the input lists.

O(max(m, n)) time, O(max(m, n)) space

C++:

```c++
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        // Create empty linked list and initialize helper variables
        int sum = 0, carry = 0, val1 = 0, val2 = 0;
        ListNode dummyHead(0);
        ListNode* l3 = &dummyHead;
      
        while (l1 || l2 || carry) {
            // Get the value of the node in each linked list
            val1 = l1 ? l1->val : 0;
            val2 = l2 ? l2->val : 0;
          
            // Calculate the sum & carry and insert into digit into the new ll
            sum = val1 + val2 + carry;
            carry = sum / 10;
            l3->next = new ListNode(sum % 10);
          
            // Point to the next node of each linked list
            l3 = l3->next;
            l1 = l1 ? l1->next : l1;
            l2 = l2 ? l2->next : l2;
        }
      
        return dummyHead.next;
    }
};
```
