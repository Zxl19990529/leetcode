### 547. 朋友圈 <h1>
### 描述<h2>
> 班上有 N 名学生。其中有些人是朋友，有些则不是。他们的友谊具有是传递性。如果已知 A 是 B 的朋友，B 是 C 的朋友，那么我们可以认为 A 也是 C 的朋友。所谓的朋友圈，是指所有朋友的集合。   
> 给定一个 N * N 的矩阵 M，表示班级中学生之间的朋友关系。如果M[i][j] = 1，表示已知第 i 个和 j 个学生互为朋友关系，否则为不知道。你必须输出所有学生中的已知的朋友圈总数。
```
示例 1:

输入: 
[[1,1,0],
 [1,1,0],
 [0,0,1]]
输出: 2 
说明：已知学生0和学生1互为朋友，他们在一个朋友圈。
第2个学生自己在一个朋友圈。所以返回2。
```
```
示例 2:

输入: 
[[1,1,0],
 [1,1,1],
 [0,1,1]]
输出: 1
```
**说明**：已知学生0和学生1互为朋友，学生1和学生2互为朋友，所以学生0和学生2也是朋友，所以他们三个在一个朋友圈，返回1。
**注意：**
```
N 在[1,200]的范围内。
对于所有学生，有M[i][i] = 1。
如果有M[i][j] = 1，则有M[j][i] = 1。
```
### 分析<h3>
> 这道题的重点在于，i和t为好友，t和j为好友，那么i和j也为好友。  
> 那么如何解决找到i和j是关键问题  
> 那么每遇到一个同学，就去找他的朋友，并找到朋友的朋友。
> 可以设立一个数组 visit来记录这n 个同学是否被拜访过  
> 如果一些同学在一个朋友圈，那这些同学都被访问过，遇到了一个没被访问过的同学，他一定是另一个朋友圈的

### 代码<h4>
```C++

class Solution {
public:
    int findCircleNum(vector<vector<int>>& M) {
        int res=0;
        vector<bool> vec(M.size(),false);
        for(int i=0;i<M.size();i++)
        {
            if(vec[i]==false)
            {
                fun(i,M,vec);
                res++;
            }
        }
        return res;
    }
    void fun(int index,vector< vector< int> > &M,vector<bool> &vec)
    {
        vec[index]=true;
        for(int i=0;i<M.size();i++)
        {
            if(M[index][i]==1 && vec[i]==false)
             fun(i,M,vec);
        }
    }
   
};
```