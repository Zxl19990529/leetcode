### Subsets <h1>
### Description<h2>
> Given a set of distinct integers, nums, return all possible subsets (the power set).

**Note:** The solution set must not contain duplicate subsets.
```
Example:

Input: nums = [1,2,3]
Output:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]
```
### Solution-回溯法 <h3>
- 对于有n个数的集合，其得到的子集比有n-1个数的子集多的子集是 有n-1个数的集合的所有子集加上第n个数
- num=[1]
  - ans=[[] 、 [1]]
- num=[1,2]
  - ans=[[] 、 [1] 、 [2],[1,2]]
- num=[1,2,3] 
  - ans=[[] 、 [1] 、 [2],[1,2] 、 [3],[1,3],[2,3],[1,2,3]]
### Code <h4>
```C++
class Solution {
public:
    vector<vector<int>> subsets(vector<int>& nums) {
        int len=nums.size();
        vector< vector<int> > res(1,vector<int>());
        if(len==0)return res;
        sort(nums.begin(),nums.end());
        for(int i=0;i<len;i++)
        {
            int res_len=res.size();
            for(int j=0;j<res_len;j++)
            {
                res.push_back(res[j]);
                res.back().push_back(nums[i]);
            }
            
        }
        return res;
    }
};
```