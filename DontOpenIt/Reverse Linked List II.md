## 92. Reverse Linked List II

Given the head of a singly linked list and two integers left and right where left <= right, reverse the nodes of the list from position left to position right, and return the reversed list.

```
class Solution {
public:
    ListNode* reverseBetween(ListNode* head, int left, int right) {
         ListNode *dummy = new ListNode(0), *pre = dummy, *cur;
            dummy->next = head;
            for (int i = 0; i < left - 1; i++){
                pre = pre->next;
            }
            cur = pre->next;
            for (int i = 0; i < right - left; i++){
                ListNode *temp = pre->next;
                pre->next = cur->next;
                cur->next = cur->next->next;
                pre->next->next = temp;
            }
            return dummy->next;
    }
};
```

If dont understood or have any better solution, lets discuss it on [discussions](https://github.com/Jimmy5467/CP/discussions). 

Star it, if helped ⭐.
