### 填充同一层的兄弟节点 II/每个节点的右向指针 II<h1>
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

> 初始状态下，所有 next 指针都被设置为 NULL。

###说明:<h3>

- 你只能使用额外常数空间。
- 使用递归解题也符合要求，本题中递归程序占用的栈空间不算做额外的空间复杂度。

###示例:<h4>
```
给定二叉树，

     1
   /  \
  2    3
 / \    \
4   5    7
```
调用你的函数后，该二叉树变为：
```
     1 -> NULL
   /  \
  2 -> 3 -> NULL
 / \    \
4-> 5 -> 7 -> NULL
```
### 分析<h5>
- 与上一个完美二叉树相比，不是每个根节点都具有左右两个子树
- 因此，不可避免的要层次遍历
- 可以利用队列，储存每个层，然后把这一层的节点连起来
### 代码<h6>
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
        queue<TreeLinkNode*> que;
        if(root==NULL)return;
        que.push(root);
        while(!que.empty())
        {
            int count=que.size();
            vector<TreeLinkNode*> temp;
            while(count--)
            {
                temp.push_back(que.front());
                if(que.front()->left)
                    que.push(que.front()->left);
                if(que.front()->right)
                    que.push(que.front()->right);
                que.pop();
            }
            for(int i=0;i<temp.size()-1;i++)
            {
                temp[i]->next=temp[i+1];
            }
            temp[temp.size()-1]->next=NULL;
        }
    }
};
```

