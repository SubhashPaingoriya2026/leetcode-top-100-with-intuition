# 04. Linked List Cycle

## 🔗 Problem Link
https://leetcode.com/problems/linked-list-cycle/

## 📌 Problem Summary
Given the head of a linked list, determine if the list contains a cycle.

Return true if there is a cycle, otherwise false.

---

## 💡 Intuition

If there is a cycle, a fast pointer moving two steps at a time
will eventually meet a slow pointer moving one step at a time.

If there is no cycle, the fast pointer will reach NULL.

This works because inside a loop, the faster pointer
will eventually lap the slower pointer.

---

## 🧠 Approach (Floyd’s Cycle Detection)

1. Initialize slow and fast pointers at head.
2. Move slow by one step.
3. Move fast by two steps.
4. If they meet → cycle exists.
5. If fast reaches NULL → no cycle.

---

## ⏱ Complexity
Time: O(n)  
Space: O(1)

---

## 💻 C++ Code (Core Logic Only)

```cpp
bool hasCycle(ListNode *head) {
    if(!head) return false;

    ListNode* slow = head;
    ListNode* fast = head;

    while(fast && fast->next){
        slow = slow->next;
        fast = fast->next->next;

        if(slow == fast)
            return true;
    }

    return false;
}
```