#### 19. Remove Nth Node From End of List
Given a linked list, remove the n-th node from the end of list and return its head.
<p align="center">
    <img src="https://github.com/asli18/leetcode/blob/master/019_example.png?raw=true" alt="019_example"/>
</p>

- 兩個pointer(cur & pn)相差n個長度，一起往前移動，當 pn到達結尾，cur->next就是要remove的node
<div style="page-break-after: always;"></div>

```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */

struct ListNode* removeNthFromEnd(struct ListNode* head, int n)
{
    struct ListNode *cur = head;
    struct ListNode *pn = head;
    
    if (head->next == NULL)
        return NULL;
    
    for (int i = n; i != 0; --i)
        pn = pn->next;
    
    if (pn == NULL) {
        head = head->next;
        return head;
    }
    
    while (pn->next != NULL) {
        pn = pn->next;
        cur = cur->next;
    }
    
    cur->next = cur->next->next;

    return head;
}
```
