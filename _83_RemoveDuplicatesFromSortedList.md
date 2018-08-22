### Remove Duplicates from Sorted List <h1>
### Description <h2>
> Given a sorted linked list, delete all duplicates such that each element appear only once.
```
Example 1:

Input: 1->1->2
Output: 1->2
```
```
Example 2:

Input: 1->1->2->3->3
Output: 1->2->3
```
### Codes <h3>
```C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {
        ListNode* root=head;
        while(head!=NULL)
        {
            while(head->next!=NULL && head->val==head->next->val)
            {
                head->next=head->next->next;
            }
            head=head->next;
        }
        return root;
    }
};
```





