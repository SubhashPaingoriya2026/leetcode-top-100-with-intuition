# 03. Remove Nth Node From End of List

## 🔗 Problem Link
https://leetcode.com/problems/remove-nth-node-from-end-of-list/

## 📌 Problem Summary
Given the head of a linked list, remove the nth node from the end and return the modified list.

---

## 💡 Intuition

If we calculate the total length first, we can remove the (length - n)th node from the start.  
But that requires two passes.

A better approach is using two pointers.  
Move the fast pointer n steps ahead.  
Then move both fast and slow together.  
When fast reaches the end, slow will be just before the node to remove.

A dummy node helps handle edge cases like removing the head.

---

## 🧠 Approach

1. Create a dummy node pointing to head.
2. Initialize slow and fast at dummy.
3. Move fast n steps forward.
4. Move both pointers until fast reaches the last node.
5. Remove slow->next.
6. Return dummy->next.

---

## ⏱ Complexity
Time: O(n)  
Space: O(1)

---

## 💻 C++ Code (Core Logic Only)

```cpp
ListNode* removeNthFromEnd(ListNode* head, int n) {
    ListNode* dummy = new ListNode(0);
    dummy->next = head;

    ListNode* slow = dummy;
    ListNode* fast = dummy;

    for(int i = 0; i < n; i++){
        fast = fast->next;
    }

    while(fast->next){
        slow = slow->next;
        fast = fast->next;
    }

    slow->next = slow->next->next;

    return dummy->next;
}
```