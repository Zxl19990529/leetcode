### N-ary Tree Preorder Traversal<h1>
### Description <h2>
> Given an n-ary tree, return the preorder traversal of its nodes' values.

For example, given a 3-ary tree:
()[https://leetcode-cn.com/static/images/problemset/NaryTreeExample.png]

Return its preorder traversal as: [1,3,5,6,2,4].
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
    vector<int> preorder(Node* root) {
       fun(vec,root);
        return vec;
    }
    void fun(vector<int> &vec,Node* root)
    {
        if(root==NULL)return ;
        vec.push_back(root->val);
        for(int i=0;i < root->children.size();i++)
        {
            preorder(root->children[i]);
        }
    }
    vector<int> vec;
};
```