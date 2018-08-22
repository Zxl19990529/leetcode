### 二叉搜索树迭代器 <h1>
### 描述<h2>
> 实现一个二叉搜索树迭代器。你将使用二叉搜索树的根节点初始化迭代器。  
> 调用 next() 将返回二叉搜索树中的下一个最小的数。  
 **注意**: next() 和hasNext() 操作的时间复杂度是O(1)，并使用 O(h) 内存，其中 h 是树的高度。
### 思路<h3>
- 基于二叉搜索树的性质（左边子树节点比根节点值小） 初始化的时候把当前根节点左边子树节点放到栈里
- 对于next() 考虑到每个左子树可能含有右子树，所以要把左子树的右子树的所有左子树再放到栈里
### 代码<h4>
```C++
/**
 * Definition for binary tree
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class BSTIterator {
public:
    stack<TreeNode*> left_vals;
    BSTIterator(TreeNode *root) {
        while(root!=NULL)
        {
            left_vals.push(root);
            root=root->left;
        }
    }

    /** @return whether we have a next smallest number */
    bool hasNext() {
        return left_vals.empty()? false:true;
    }

    /** @return the next smallest number */
    int next() {
            TreeNode* temp=left_vals.top();
            left_vals.pop();
            int ans=temp->val;
            temp=temp->right;
            while(temp)
            {
                left_vals.push(temp);
                temp=temp->left;
            }
        return ans;
    }
};

/**
 * Your BSTIterator will be called like this:
 * BSTIterator i = BSTIterator(root);
 * while (i.hasNext()) cout << i.next();
 */
```