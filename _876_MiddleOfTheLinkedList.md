# Middle of the Linked List 

## Description

> Given a non-empty, singly linked list with head node head, return a middle node of linked list. If there are two middle nodes, return the second middle node.

### Example 1:
```vb
Input: [1,2,3,4,5]
Output: Node 3 from this list (Serialization: [3,4,5])
The returned node has value 3.  (The judge's serialization of this node is [3,4,5]).
Note that we returned a ListNode object ans, such that:
ans.val = 3, ans.next.val = 4, ans.next.next.val = 5, and ans.next.next.next = NULL.
```
### Example 2:
```vb
Input: [1,2,3,4,5,6]
Output: Node 4 from this list (Serialization: [4,5,6])
Since the list has two middle nodes with values 3 and 4, we return the second one.
 ```

**Note:**
- The number of nodes in the given list will be between 1 and 100.

### Code 史上最快，有可能成为范例，新的出题目
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
    ListNode* middleNode(ListNode* head) {
        ListNode* p=head;//滞后跟踪法
        bool flag=false;
        while(head!=NULL)
        {
            head=head->next;
            if(flag)
            {
                p=p->next;
                flag=false;
                continue;
            }
            flag=true;
        }
        return p;
    }
};
```