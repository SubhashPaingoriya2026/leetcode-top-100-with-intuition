# 05. Merge Two Sorted Lists

## 🔗 Problem Link
https://leetcode.com/problems/merge-two-sorted-lists/

## 📌 Problem Summary
You are given the heads of two sorted linked lists.
Merge the two lists into one sorted list and return its head.

---

## 💡 Intuition

Since both lists are already sorted, we can compare their current nodes
and attach the smaller one to the merged list.

This is similar to the merge step in Merge Sort.

Using a dummy node simplifies handling the head of the new list.

---

## 🧠 Approach

1. Create a dummy node.
2. Maintain a pointer `temp` for building the merged list.
3. Compare nodes of both lists:
   - Attach the smaller node.
   - Move that list forward.
4. If one list finishes, attach the remaining part of the other list.
5. Return `dummy->next`.

---

## ⏱ Complexity
Time: O(n + m)  
Space: O(1)

---

## 💻 C++ Code (Core Logic Only)

```cpp
ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
    ListNode* dummy = new ListNode(0);
    ListNode* temp = dummy;

    while(list1 && list2){
        if(list1->val <= list2->val){
            temp->next = list1;
            list1 = list1->next;
        } else {
            temp->next = list2;
            list2 = list2->next;
        }
        temp = temp->next;
    }

    if(list1) temp->next = list1;
    if(list2) temp->next = list2;

    return dummy->next;
}
```