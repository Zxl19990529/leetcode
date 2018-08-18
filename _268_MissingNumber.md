# Missing Number
## Description
> Given an array containing n distinct numbers taken from 0, 1, 2, ..., n, find the one that is missing from the array.
```c
Example 1:

Input: [3,0,1]
Output: 2
```
```c
Example 2:

Input: [9,6,4,2,3,5,7,0,1]
Output: 8
```

**Note:**
- Your algorithm should run in linear runtime complexity. Could you implement it using only constant extra space complexity?
```c++
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int sum=0;
        int n=nums.size();
        for(auto i:nums)
            sum+=i;
        int sum_true=(1+n)*n/2;
        return sum_true-sum;
    }
};
```

