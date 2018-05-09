### Insert into a Binary Search Tree<h1>
### Description <h2>
> Given the root node of a binary search tree (BST) and a value to be inserted into the tree, insert the value into the BST. Return the root node of the BST after the insertion. It is guaranteed that the new value does not exist in the original BST.  
> Note that there may exist multiple valid ways for the insertion, as long as the tree remains a BST after insertion. You can return any of them.

### 样例 <h5>
```
Given the tree:
        4
       / \
      2   7
     / \
    1   3
And the value to insert: 5
```
```
You can return this binary search tree:

         4
       /   \
      2     7
     / \   /
    1   3 5

This tree is also valid:

         5
       /   \
      2     7
     / \   
    1   3
         \
          4
```

### 分析<h3>
> 根据搜索二叉树的性质，可以直接找到外节点，然后插入即可  
> 但是要注意用temp来储存上一个节点
### 代码<h4>
```C++
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    TreeNode* insertIntoBST(TreeNode* root, int val) {
        TreeNode* head=root;
        TreeNode* temp;
        int temp_towards;
        if(root==NULL)return NULL;
        while(root)
        {
            if(root->val < val )
            {
                temp=root;
                temp_towards=0;
                root=root->right;                
            }
            else if(val < root->val)
            {
                temp=root;
                temp_towards=1;
                root=root->left;
            }
        }
        root=new TreeNode(val);
        if(temp_towards==1)
        {
            temp->left=root;
        }
        else 
        {
            temp->right=root;
        }
        return head;
    }
};
```