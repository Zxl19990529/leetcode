### 每个节点的右向指针/填充同一层的兄弟节点<h1>
### 描述<h2>
> 给定一个二叉树  
```
struct TreeLinkNode {
  TreeLinkNode *left;
  TreeLinkNode *right;
  TreeLinkNode *next;
}
```
> 填充它的每个 next 指针，让这个指针指向其下一个右侧节点。如果找不到下一个右侧节点，则将 next 指针设置为 NULL。

初始状态下，所有 next 指针都被设置为 NULL。

###说明:<h3>

- 你只能使用额外常数空间。
- 使用递归解题也符合要求，本题中递归程序占用的栈空间不算做额外的空间复杂度。
- 你可以假设它是一个完美二叉树（即所有叶子节点都在同一层，每个父节点都有两个子节点）。
示例:
```
给定完美二叉树，

     1
   /  \
  2    3
 / \  / \
4  5  6  7
调用你的函数后，该完美二叉树变为：

     1 -> NULL
   /  \
  2 -> 3 -> NULL
 / \  / \
4->5->6->7 -> NULL
```
### 分析<h4>
- 递归的方法在这里得到了充分应用
一开始，我的思路是判断每个根节点的右边，用栈来储存当前的节点然后pop掉  
在往右连接，每个子树用NULL来分割，但是写着写着就混乱了，调试也很不方便  
瞄了一眼网上的代码，茅塞顿开！！！  判断每个根节点的子节点，因为是完美的  
二叉树，所以左右一定有子树，直接连接每个根节点的左右子树即可，然后分别  
往左右子树进入，从而递归
### 代码<h5>
```C++
/**
 * Definition for binary tree with next pointer.
 * struct TreeLinkNode {
 *  int val;
 *  TreeLinkNode *left, *right, *next;
 *  TreeLinkNode(int x) : val(x), left(NULL), right(NULL), next(NULL) {}
 * };
 */
class Solution {
public:
    void connect(TreeLinkNode *root) {
        if(root==NULL)return ;
        if(root->left!=NULL)
            root->left->next=root->right;
        if(root->right!=NULL)
            root->right->next=  root->next==NULL? NULL:root->next->left;
        connect(root->left);
        connect(root->right);
    }
};
```
