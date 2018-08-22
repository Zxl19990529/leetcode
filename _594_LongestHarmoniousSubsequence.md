### 594. 最长和谐子序列 <h1>
### 描述 <h2>
> 和谐数组是指一个数组里元素的最大值和最小值之间的差别正好是1。  
> 现在，给定一个整数数组，你需要在所有可能的子序列中找到最长的和谐子序列的长度。
```
示例 1:

输入: [1,3,2,2,5,2,3,7]
输出: 5
原因: 最长的和谐数组是：[3,2,2,2,3].
```
**说明** : 输入的数组长度最大不超过20,000.
### 分析<h3>
- 根据map平衡树的特性，可以考虑把数字 放入map，第二个位置记录出现次数
- 用两个迭代器从头遍历，每次判断是前后迭代器的数字是否和谐，如果和谐就比较当前结果和当前长度
- 返回最大的结果即可
### 代码<h4>
```C++
class Solution {
public:
    int findLHS(vector<int>& nums) {
        if(nums.size()==0)return 0;
        int res=0;
        map<int,int> mp;
        for(int i=0;i<nums.size();i++)
        {
            ++mp[nums[i]];
        }
        auto it_1=mp.begin();
        auto it_2=it_1;
        it_2++;
        while(it_2!=mp.end())
        {
            if(it_1->first+1==it_2->first)
                res=max(res,it_1->second+it_2->second);
            it_1++;it_2++;
        }
        return res;
    }
};
```