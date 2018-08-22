### 114. 二叉树展开为链表<h1>
### 描述<h2>
> 给定一个二叉树，原地将它展开为链表。
```
例如，给定二叉树

    1
   / \
  2   5
 / \   \
3   4   6

将其展开为：

1
 \
  2
   \
    3
     \
      4
       \
        5
         \
          6
```
### 分析<h3>
- 一开是的思路是前序遍历，然后构造链表，但是效率一般
- 仔细发现，是这样操作的：
  - 把左边子树 整体塞到右边子树和根节点之间
  - 从最左边开始往右推进即可
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
static int x = []() { 
    std::ios::sync_with_stdio(false); 
    cin.tie(NULL);  
    return 0; 
}();
class Solution {
public:
    void flatten(TreeNode* root) {
        if(root==NULL)return;
        if(root->left)flatten(root->left);//可劲往左走
        if(root->right)flatten(root->right);//可劲往右走
        //这里走到头了，取单个节点分析
        TreeNode* temp;
        temp=root->right;
        root->right=root->left;
        root->left=NULL;
        TreeNode* p=root;
        while(p->right!=NULL)p=p->right;
        p->right=temp;
    }
};
```
### 解法2（非递归）<h4>
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
static int x = []() { 
    std::ios::sync_with_stdio(false); 
    cin.tie(NULL);  
    return 0; 
}();
class Solution {
public:
    void flatten(TreeNode* root) {
        while(root)
        {
            if(root->left)
            {
                TreeNode* temp=root->left;
                TreeNode* temp_2=root->right;
                while(temp->right)temp=temp->right;
                root->right=root->left;
                root->left=NULL;
                temp->right=temp_2;
            }
            root=root->right;
        }
    }
};
```
