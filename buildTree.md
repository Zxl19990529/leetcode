### 从中序与后序遍历序列构造二叉树<h1>
### 描述<h2>
> 根据一棵树的中序遍历与后序遍历构造二叉树。

**注意:**
> 你可以假设树中没有重复的元素。
```
例如，给出

中序遍历 inorder = [9,3,15,20,7]
后序遍历 postorder = [9,15,7,20,3]
返回如下的二叉树：

    3
   / \
  9  20
    /  \
   15   7
```
### 代码+注释 8（ms）<h3>
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
    TreeNode* buildTree(vector<int>& inorder, vector<int>& postorder) {
        stack<TreeNode*> st;   //用栈来储存当前根节点
        if(inorder.size()==0)return NULL;
        int t=postorder.back();
        TreeNode* root;
        root=new TreeNode(t);
        
        postorder.pop_back();
        st.push(root);
        while(true)
        {// 思想是 以后序遍历为根节点的母表
        // 从postorder的后面开始遍历，每个节点当做根节点，通过inorder来进行判断下一个根节点放在这个
        // 根节点的左边还是右边
            if(st.top()->val!=inorder.back())
            {
                TreeNode *p=new TreeNode(postorder.back());
                postorder.pop_back();
                st.top()->right=p;
                st.push(p);
            }
            else
            {
                TreeNode *temp=st.top();
                st.pop();
                inorder.pop_back();
                if(inorder.size()==0)break;
                if(st.size() && inorder.back()==st.top()->val)
                    continue;
                temp->left=new TreeNode(postorder.back());
                postorder.pop_back();
                st.push(temp->left);
            }
        }
        return root;
    }
};
```
