### Maximum Depth of N-ary Tree <h1>
### Description <h2>
> Given a n-ary tree, find its maximum depth.  
The maximum depth is the number of nodes along the longest path from the  
 root node down to the farthest leaf node.

For example, given a 3-ary tree:
![](https://leetcode-cn.com/static/images/problemset/NaryTreeExample.png)
```
We should return its max depth, which is 3.
```
### Note:<h3>
- The depth of the tree is at most 1000.
- The total number of nodes is at most 5000.
### Codes(52ms) 该题史上最快的递归<h4>
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
    int maxDepth(Node* root) {
        int res=0;
        if(root==NULL)return 0;
        int size_=root->children.size();
        for(int i=0;i<size_;i++)
        {
            res=max(res,maxDepth(root->children[i]));
        }
        return res+1;
    }
};
```
