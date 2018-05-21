### 136.只出现 一次的数字<h1>
### 描述 <h2>
> 给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。  
**说明**：
- 你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？
```
示例 1:

输入: [2,2,1]
输出: 1
```
```
示例 2:

输入: [4,1,2,1,2]
输出: 4
```
```C++
map<int,int> mp;
        for(int i=0;i<nums.size();i++)
        {
            if(mp.find(nums[i])==mp.end())
                mp[nums[i]]=1;
            else 
                mp[nums[i]]++;
        }
        auto it=mp.begin();
        while(it!=mp.end())
        {
            if(it->second==1)return it->first;
            it++;
        }
```
```C++
class Solution {
public:
    int singleNumber(vector<int>& nums) {
        // 0 异或任何数=任何数
        // 任何数 异或 任何数自身 =0
        // 1 异或 任何数=任何数的相反数
        // A 异或 B两次，得到A本身
        int num=0;
        for(int i=0;i<nums.size();i++)
        {
            num=num^nums[i];
        }
        return num;
    }
};
```