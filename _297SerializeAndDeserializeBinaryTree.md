###  二叉树的序列化与反序列化<h1>
### 描述<h2>
> 序列化是将一个数据结构或者对象转换为连续的比特位的操作，进而可以将转换后的数据存储在一个文件或者内存中，同时也可以通过网络传输到另一个计算机环境，采取相反方式重构得到原数据。  
> 请设计一个算法来实现二叉树的序列化与反序列化。这里不限定你的序列/反序列化算法执行逻辑，你只需要保证一个二叉树可以被序列化为一个字符串并且这个字符串可以被反序列化得到一个原始的树结构。

例如，你可以序列化下面的二叉树：
```
    1
   / \
  2   3
     / \
    4   5
```
> 得到 "[1,2,3,null,null,4,5]"，这与LeetCode目前使用的方式一致 how LeetCode OJ serializes a binary tree。你并非必须采取这种方式，你也可以创造性的用其他的方式解决这个问题。

- 小贴士: 不要使用类的成员/全局/静态变量来存储状态机，你的序列化和反序列化算法应该是无状态机的。
### 新技能<h5>
- stoi("string类型")  把string类型的数字转成真正的数字
- instringstream 把string类型的数据存入缓冲区，方便自动逐个读取
### 分析<h4>
- 这是一个困难级别的题目，几乎花了我一下午
- 我们分两步
  - 序列化
    - 这里用到了之前练过的层序遍历
    - 但是不同的是，由于data里面有null（题中用string类型的"#"来表示），所以所有的TreeNode* 都要加入队列
    - 把每个节点处的值转化成string类型连接起来，用“ ”来分隔
  - 反序列化
    - 反序列化是个难点
    - 这里学会了一个新技能（instringstream)，把data存入缓冲区，就可以自动往后取值，就省去了用vector遍历的麻烦
    - 这里要注意的是 先制造左树，再制造右树，每次制造完之后都要检查instringstream是否已经到了结尾，到结尾了就break
### 代码 <h6>
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
class Codec {
public:

    // Encodes a tree to a single string. 
    string serialize(TreeNode* root) {
        //这里应该是层序遍历
        string res="";
        if(root==NULL)return res;
        queue<TreeNode*> q;
        q.push(root);
        while(!q.empty())
        {
            if(q.front())
            {
                res+=to_string((q.front()->val));
                res.append(" ");
                q.push(q.front()->left);
                q.push(q.front()->right);
            }
            else
            {
                res.append("# ");
            }
            q.pop();
        }
        return res;
    }

    // Decodes your encoded data to tree.
    TreeNode* deserialize(string data) {
        if(data.empty())return NULL;
        istringstream get_(data);
        queue<TreeNode*> q;
        string val;
        get_ >> val;
        TreeNode* res=new TreeNode(stoi(val));
        TreeNode* temp=res;
        q.push(temp);
        while(!q.empty())
        {
            if(!(get_ >> val))break;
            if(val!="#")
            {
                temp=new TreeNode(stoi(val));
                q.push(temp);
                q.front()->left=temp;
            }
            if(!(get_ >> val))break;
            if(val!="#")
            {
                temp=new TreeNode(stoi(val));
                q.front()->right=temp;
                q.push(temp);
            }
            q.pop();
        }
        return res;
    }
};

// Your Codec object will be instantiated and called as such:
// Codec codec;
// codec.deserialize(codec.serialize(root));
```