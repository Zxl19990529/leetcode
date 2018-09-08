# 33. Search in Rotated Sorted Array

## Description
> Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.  
> (i.e., [0,1,2,4,5,6,7] might become [4,5,6,7,0,1,2]).  
> You are given a target value to search. If found in the array return its index, otherwise return -1.  
> You may assume no duplicate exists in the array.  

- Your algorithm's runtime complexity must be in the order of O(log n).
```
Example 1:

Input: nums = [4,5,6,7,0,1,2], target = 0
Output: 4
```
```
Example 2:

Input: nums = [4,5,6,7,0,1,2], target = 3
Output: -1
```
## Code
```c++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        auto it=find(nums.begin(),nums.end(),target);
        if(it==nums.end())return -1;
        return std::distance(nums.begin(),it);
    }
};
```
## Code 2
```c++
class Solution {
public:
    int search(vector<int>& nums, int target) {
        int len = nums.size();
        int left = 0, right = len - 1;
        while(left <= right) {
            int middle = (left + right) / 2;
            if(nums[middle] == target)
                return middle;
            if(nums[middle] >= nums[left] && nums[middle] > nums[right]) {
                if(target > nums[middle]) {
                    left = middle + 1;
                }
                else {
                    if(target < nums[left]) {
                        left = middle + 1;
                    }
                    else {
                        right = middle - 1;
                    }
                }
            }
            else if(nums[middle] < nums[left] && nums[middle] <= nums[right]) {
                if(target > nums[middle]) {
                    if(target > nums[right]) {
                        right = middle - 1;
                    }
                    else {
                        left = middle + 1;
                    }
                }
                else {
                    right = middle - 1;
                }
            }
            else {
                if(target > nums[middle]) {
                    left++;
                }
                else {
                    right--;
                }
            }
        }
        return -1;
    }
};
```