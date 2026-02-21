# Reverse Linked List

## 🔗 Problem Link
https://leetcode.com/problems/reverse-linked-list/

## 💡 Intuition

Brute force thinking:
If we reverse pointers one by one, we can flip direction.

Key observation:
Each node should point to its previous node instead of next.

## 🧠 Approach

Use three pointers:
- prev
- curr
- next

Iteratively reverse links.

## ⏱ Complexity
Time: O(n)
Space: O(1)

## 💻 C++ Code (Core Logic Only)

```cpp
ListNode* reverseList(ListNode* head) {
    ListNode* prev = NULL;
    ListNode* curr = head;

    while(curr){
        ListNode* next = curr->next;
        curr->next = prev;
        prev = curr;
        curr = next;
    }
    return prev;
}