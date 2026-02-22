# 06. Linked List Cycle II

## 🔗 Problem Link
https://leetcode.com/problems/linked-list-cycle-ii/

## 📌 Problem Summary
Given the head of a linked list, return the node where the cycle begins.
If there is no cycle, return NULL.

---

## 💡 Intuition

First, detect whether a cycle exists using slow and fast pointers.

If they meet, a cycle exists.

To find the starting node:
Reset one pointer to head.
Move both pointers one step at a time.
They will meet exactly at the start of the cycle.

This works because the distance from head to cycle start
equals the distance from meeting point to cycle start.

---

## 🧠 Approach

1. Use slow and fast pointers to detect cycle.
2. If they never meet → return NULL.
3. If they meet:
   - Reset slow to head.
   - Move both one step at a time.
4. The node where they meet again is the cycle start.

---

## ⏱ Complexity
Time: O(n)  
Space: O(1)

---

## 💻 C++ Code (Core Logic Only)

```cpp
ListNode *detectCycle(ListNode *head) {
    if(!head) return NULL;

    ListNode* slow = head;
    ListNode* fast = head;

    while(fast && fast->next){
        slow = slow->next;
        fast = fast->next->next;

        if(slow == fast){
            slow = head;

            while(slow != fast){
                slow = slow->next;
                fast = fast->next;
            }
            return slow;
        }
    }

    return NULL;
}
```