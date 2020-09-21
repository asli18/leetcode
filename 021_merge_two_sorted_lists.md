#### 21. Merge Two Sorted Lists
Merge two sorted linked lists and return it as a new sorted list. The new list should be made by splicing together the nodes of the first two lists.
<p align="center">
    <img src="https://github.com/asli18/leetcode/blob/master/021_example.png?raw=true" alt="021_example"/>
</p>

- 比大小，然後延用原本的 list 實體
<div style="page-break-after: always;"></div>

```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode* mergeTwoLists(struct ListNode* l1, struct ListNode* l2)
{
    struct ListNode *head, *cur;

    if ((l1 == NULL) && (l2 == NULL))
        return NULL;

    if (l1 == NULL)
        return l2;
    if (l2 == NULL)
        return l1;

    if (l1->val < l2->val) {
        head = l1;
        l1 = l1->next;
    } else {
        head = l2;
        l2 = l2->next;
    }
    cur = head;

    while ((l1 != NULL) || (l2 != NULL)) {
        if ((l1 != NULL) && (l2 != NULL)) {
            if (l1->val < l2->val) {
                cur->next = l1;
                l1 = l1->next;
            } else {
                cur->next = l2;
                l2 = l2->next;
            }
        } else if (l1 != NULL) {
            cur->next = l1;
            l1 = l1->next;
            break;
        } else {
            cur->next = l2;
            l2 = l2->next;
            break;
        }
        cur = cur->next;
    }
    return head;
}
```
