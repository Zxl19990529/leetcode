#  Find First and Last Position of Element in Sorted Array
## Description
> Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.  
> Your algorithm's runtime complexity must be in the order of O(log n).  
> If the target is not found in the array, return [-1, -1].  

```
Example 1:

Input: nums = [5,7,7,8,8,10], target = 8
Output: [3,4]
```
```
Example 2:

Input: nums = [5,7,7,8,8,10], target = 6
Output: [-1,-1]
```
## Code
```c++
class Solution {
public:
    vector<int> searchRange(vector<int>& nums, int target) {
        vector<int> res={-1,-1};
        vector<int>::iterator it_1=find(nums.begin(),nums.end(),target);
        if(it_1==nums.end())
            return res;
        vector<int>::iterator it_2=nums.end()-1;
        for(;*it_2!=target;it_2--);
        
        res[0]=distance(nums.begin(),it_1);
        res[1]=nums.size()-distance(it_2,nums.end());
        return res;
    }
};
```
