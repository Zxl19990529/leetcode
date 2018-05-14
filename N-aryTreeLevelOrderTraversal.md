### N-ary Tree Level Order Traversal<h1>
### Description <h2>
>  Given an n-ary tree, return the level order traversal of its nodes' values. (ie, from left to right, level by level).

For example, given a 3-ary tree:

()[https://leetcode-cn.com/static/images/problemset/NaryTreeExample.png]
We should return its level order traversal:
```
[
     [1],
     [3,2,4],
     [5,6]
]
```
### Note: <h3>

   - The depth of the tree is at most 1000.
   - The total number of nodes is at most 5000.
### 代码 <h4>
```C++
/*
// Definition for a Node.
class Node {
public:
    int val = NULL;
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
    vector<vector<int>> levelOrder(Node* root) {
        vector<vector<int> > res;
        if(root==NULL)return res;
        queue<Node*> qu;
        qu.push(root);
        while(!qu.empty())
        {
            vector<int> temp;
            int size=qu.size();
            for(int i=0;i<size;i++)
            {
                Node* p=qu.front();
                for(int i=0;i< p->children.size();i++)
                {
                    qu.push(p->children[i]);
                }
                temp.push_back(p->val);
                qu.pop();                
            }
            res.push_back(temp);
        }
        return res;
    }
};
```
