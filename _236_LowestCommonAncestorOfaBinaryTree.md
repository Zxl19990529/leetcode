### 236 二叉树的最近公共祖先<h1>
### 描述<h2>
> 给定一棵二叉树, 找到该树中两个指定节点的最近公共祖先。

> 百度百科中最近公共祖先的定义： “对于有根树T的两个结点u、v，最近公共祖先表示一个结点x，满足x是u、v的祖先且x的深度尽可能大。”（一个节点也可以是它自己的祖先）
```
       _______3______
      /              \
   ___5__          ___1__
  /      \        /      \
  6      _2       0       8
        /  \
        7   4
例如，节点5和节点1的最近公共祖先是节点3；节点5和节点4的最近公共祖先是节点5，因为根据定义，一个节点可以是它自己的祖先。
```
### 分析<h3>
- 可以通过前寻找路径的方法，把两个节点的路径得到
- 然后比较路径，由于有共同祖先，所以，而这路径的开始有一部分是相同的
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
    vector<TreeNode*> fa1;
    vector<TreeNode*> fa2;

    void get_path(vector<TreeNode*> &fa, TreeNode* root, TreeNode* p, TreeNode* q)
    {

        if (root == p){
            fa1 .assign(fa.begin(),fa.end()) ;
        }
        if (root == q){
            fa2 .assign(fa.begin(),fa.end());
        }

        if (root->left != NULL){
            fa.push_back(root->left);
            get_path(fa,root->left, p,q);
            fa.pop_back();
        }
        if (root->right != NULL)
        {
            fa.push_back(root->right);
            get_path(fa, root->right, p,q);
            fa.pop_back();
        }
    }

    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        vector<TreeNode*> fa;
        fa.push_back(root);
        get_path(fa, root, p,q);

        vector<TreeNode*>::iterator it1 = fa1.begin();
        vector<TreeNode*>::iterator it2 = fa2.begin();

        TreeNode* res;

        while (it1 != fa1.end() && it2 != fa2.end())
        {
            if (*it1 == *it2)
            {
                res = *it1;
                it1++;
                it2++;
            }
            else
            {
                break;
            }
        }

        return res;
    }
};
```
