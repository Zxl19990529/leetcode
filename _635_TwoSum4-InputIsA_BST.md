### 653. 两数之和 IV - 输入 BST<h1>
### 描述<h2>
> 给定一个二叉搜索树和一个目标结果，如果 BST 中存在两个元素且它们的和等于给定的目标结果，则返回 true。

案例 1:
```
输入:
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9
输出: True
 ```
案例 2:
```
输入:
    5
   / \
  3   6
 / \   \
2   4   7

Target = 28
输出: False
```
### 分析<h3>
> 这题不难，用到了二叉搜索树的搜索，然后二分查找即可
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
    bool findTarget(TreeNode* root, int k) {
        vector<int> vec;
        fun(vec,root);
        sort(vec.begin(),vec.end());
        int size=vec.size();
        if(size<2)return false;
        if(k>= 2*vec[size-1])
            return false;
        int left=0,right=size-1;
        while(left<right)
        {
            if(vec[left]+vec[right]==k)return true;
            if(vec[left]+vec[right]<k)
                left++;
            else  right--;
        }
        return false;
    }
    void fun(vector<int>& vec,TreeNode* root)
    {
        if(root==NULL)return ;
        vec.push_back(root->val);
        fun(vec,root->left);
        fun(vec,root->right);
    }
};
```
