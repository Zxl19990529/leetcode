### 删除二叉搜索树中的节点<h1>
### 描述<h2>
> 给定一个二叉搜索树的根节点 root 和一个值 key，删除二叉搜索树中的 key 对应的节点，并保证二叉搜索树的性质不变。返回二叉搜索树（有可能被更新）的根节点的引用。  
> 一般来说，删除节点可分为两个步骤：

    - 首先找到需要删除的节点；
    - 如果找到了，删除它。  
说明： 要求算法时间复杂度为 O(h)，h 为树的高度。
### 分析<3>
> 第一遍思路是搜索二叉树找到目标节点，父节点，然后删除目标节点后直接连上  
> 但是还要考虑根节点的左右子节点，左子树直接连上，但是右子树就不好办了  
> 这里回头看到了一遍序言，发现可以通过先把目标节点和目标节点右子树的左端点交换，然后在删除没有子树的节点
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
    TreeNode* deleteNode(TreeNode* root, int key) {
        if (!root) 
        {
            return root;
        }
        if (root->val == key)
        {
            // 找到值相同节点，开始删除
            if (!root->right) 
            {
                // 树没有右节点，这种情况就是到端点了
                return root->left;
            }
            TreeNode *ptr = root->right;
            // 因为这一步开始是把目标节点交换到右子树左端点
            while (ptr->left) 
            {
                ptr = ptr->left;
            }
            std::iter_swap(&root->val, &ptr->val);
        }
        root->left = deleteNode(root->left, key);//用来找到目标节点
        root->right = deleteNode(root->right, key);
        return root;
    }
};
```