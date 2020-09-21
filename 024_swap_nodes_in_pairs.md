#### 24. Swap Nodes in Pairs
Given a linked list, swap every two adjacent nodes and return its head.
You may not modify the values in the list's nodes, only nodes itself may be changed.
<p align="center">
    <img src="https://github.com/asli18/leetcode/blob/master/024_example.png?raw=true" alt="024_example"/>
</p>

- pointer 兩兩交換，存前一組的結尾`(prev)`，再接到當下這組

```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */

struct ListNode* swapPairs(struct ListNode* head)
{
    if (head == NULL)
        return NULL;
    struct ListNode *cur = head;
    struct ListNode *prev = head, *next;

    if (cur->next != NULL)
        head = cur->next;

    while (cur != NULL && cur->next != NULL) {
        prev->next = cur->next;

        next = cur->next->next;
        cur->next->next = cur;
        cur->next = next;

        prev = cur;
        cur = cur->next;
    }

    return head;
}
```
