### N-ary Tree Postorder Traversal<h1>
### Description <h2>
> Given an n-ary tree, return the postorder traversal of its nodes' values.

For example, given a 3-ary tree:

()[https://leetcode-cn.com/static/images/problemset/NaryTreeExample.png]
Return its postorder traversal as: [5,6,3,2,4,1].
### 代码<h3>
```C++
/*
// Definition for a Node.
class Node {
public:
    int val;
    vector<Node*> children;

    Node() {}

    Node(int _val, vector<Node*> _children) {
        val = _val;
        children = _children;
    }
};
*/
class Solution {
public:
    vector<int> postorder(Node* root) {
        fun(vec,root);
        return vec;
    }
    void fun(vector<int>& vec,Node* root)
    {
        if(root==NULL)return;
        for(int i=0;i<root->children.size();i++)
        {
            fun(vec,root->children[i]);
        }
        vec.push_back(root->val);
    }
    vector<int> vec;
};
```
