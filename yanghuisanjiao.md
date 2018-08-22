### 杨辉三角<h1>
### 描述<h2>
> 给定一个非负整数 numRows，生成杨辉三角的前 numRows 行。

- 示例:
```
输入: 5
输出:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```
###代码<h3>
```C++
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int> > res;
        if(numRows==0)return res;
        for(int row=1;row<=numRows;row++)
        {
            vector<int> temp(row,1);
            for(int i=1;i<row-1;i++)
            {
                temp[i]=res[row-2][i]+res[row-2][i-1];
            }
            res.push_back(temp);
        }
        return res;
    }
   
};
```

