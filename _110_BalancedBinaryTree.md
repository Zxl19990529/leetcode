### 平衡二叉树<h1>
### 描述<h2>
> 给定一个二叉树，判断它是否是高度平衡的二叉树。  
本题中，一棵高度平衡二叉树定义为：  
一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过1。  

示例 1:
```
给定二叉树 [3,9,20,null,null,15,7]

    3
   / \
  9  20
    /  \
   15   7
返回 true 。
```
示例 2:
```
给定二叉树 [1,2,2,3,3,null,null,4,4]

       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
返回 false 。
```
### 分析<h3>
- 可以考虑用递归法
- 对于判断一个二叉树是否平衡，就要看左右子树高度差是否 大于1
- 如果左右子树高度差大于1了，那么这个根节点 不平衡
- 如果左右子树有一个 不平衡那么根节点也不平衡
- 判断条件是 只要有一个不平衡，那就不平衡
### 代码(4ms)<h4>
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
static auto x = [](){
    std::ios::sync_with_stdio(false);
    std::cin.tie(NULL);
    return 0;
}();
class Solution {
public:
    bool isBalanced(TreeNode* root) {
        if(root==NULL)return true;
        return fun(root)>=0;
    }
    int fun(TreeNode* root)
    {
        if(root==NULL)return 0;
        int left=fun(root->left);
        int right=fun(root->right);
        if(abs(left-right)>1 || left<0 || right<0)
        {
            return -1;
        }
        return max(left,right)+1;
    }
};
```
