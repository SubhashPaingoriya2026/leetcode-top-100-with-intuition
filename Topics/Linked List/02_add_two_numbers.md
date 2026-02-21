# 02. Add Two Numbers

## 🔗 Problem Link
https://leetcode.com/problems/add-two-numbers/

## 📌 Problem Summary
Two non-empty linked lists represent two non-negative integers.
Digits are stored in reverse order.
Return the sum as a linked list.

---

## 💡 Intuition

This problem is similar to elementary addition.
We traverse both lists simultaneously and add corresponding digits.
If the sum exceeds 9, we maintain a carry.
We continue until both lists are finished and no carry remains.
A dummy node helps simplify list construction.

---

## 🧠 Approach

1. Initialize a dummy node.
2. Maintain a carry variable.
3. Traverse both lists:
   - Add values and carry.
   - Create new node with (sum % 10).
   - Update carry = sum / 10.
4. Return dummy->next.

---

## ⏱ Complexity
Time: O(max(n, m))  
Space: O(1) (excluding output list)

---

## 💻 C++ Code (Core Logic Only)

```cpp
ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        ListNode* dummyNode = new ListNode(-1);
        ListNode* currNode = dummyNode;
        int carry = 0 , sum = 0; 
        while(l1 != NULL && l2 != NULL){
            int x = (l1->val + l2->val) + carry;
            sum = x%10;
            carry = x/10;
            ListNode* newNode = new ListNode(sum);
            currNode->next = newNode;
            currNode = newNode;
            l1 = l1->next;
            l2 = l2->next;
        }

        while(l1){
            int x = (l1->val) + carry;
            sum = x%10;
            carry = x/10;
            ListNode* newNode = new ListNode(sum);
            currNode->next = newNode;
            currNode = newNode;
            l1 = l1->next;
        }

        while(l2){
            int x = (l2->val) + carry;
            sum = x%10;
            carry = x/10;
            ListNode* newNode = new ListNode(sum);
            currNode->next = newNode;
            currNode = newNode;
            l2 = l2->next;
        }

        if(carry != 0){
            ListNode* newNode = new ListNode(carry);
            currNode->next = newNode;
            currNode = newNode;
        }
        return dummyNode->next;
    }
```