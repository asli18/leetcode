#### 160. Intersection of Two Linked Lists
Write a program to find the node at which the intersection of two singly linked lists begins.
<p align="center">
    <img src="https://github.com/asli18/leetcode/blob/master/160_example.png?raw=true" alt="160_example" width="440" height="280"/>
</p>
- 尋找交錯點，沒找到回傳 NULL
    - Example
        - A: `1 9 1 2 4 N 3 *2* 4`
        - B: `3 2 4 N 1 9 1 *2* 4`
```c
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     struct ListNode *next;
 * };
 */
struct ListNode *getIntersectionNode(struct ListNode *headA,
                                     struct ListNode *headB)
{
    struct ListNode *p1 = headA;
    struct ListNode *p2 = headB;

    while (p1 != p2) {
        p1 = p1 ? p1->next : headB;
        p2 = p2 ? p2->next : headA;
    }
    return p1;
}
```