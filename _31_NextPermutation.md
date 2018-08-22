#  Next Permutation
## Description
> Implement next permutation, which rearranges numbers into the lexicographically next greater permutation of numbers.  
> If such arrangement is not possible, it must rearrange it as the lowest possible order (ie, sorted in ascending order).  
> The replacement must be in-place and use only constant extra memory.

> Here are some examples. Inputs are in the left-hand column and its corresponding outputs are in the right-hand column.
```c++
1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1
```
## Solution
![](https://leetcode-cn.com/media/original_images/31/31_Next_Permutation.gif)
## Codes
```c++
class Solution {
public:
    void nextPermutation(vector<int>& nums) {
        int len=nums.size();
        int i;
        for(i=len-2;i>=0 && nums[i+1]<nums[i];i--);//找到第一个降序值
        
        if(i>=0)
        {
            int j=len-1;
            while(j >= 0 && nums[j] <= nums[i])// 找到刚好比i处大的值
            {
                j--;
            }
            my_swap(&nums[i],&nums[j]);
        }
        my_reverse(nums,i+1,len-1);
    }
    void my_swap(int* i,int* j)
    {
        int temp=*i;
        *i=*j;
        *j=temp;
    }
    void my_reverse(vector<int>& nums,int i,int j)
    {
        while(i<j)
        {
            my_swap(&nums[i],&nums[j]);
            i++;j--;
        }
    }
};
```