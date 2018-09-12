# Find K Closest Elements

## Description
> Given a sorted array, two integers k and x, find the k closest elements to x in the array. The result should also be sorted in ascending order. If there is a tie, the smaller elements are always preferred.
```
Example 1:
Input: [1,2,3,4,5], k=4, x=3
Output: [1,2,3,4]
```
```
Example 2:
Input: [1,2,3,4,5], k=4, x=-1
Output: [1,2,3,4]
```
**Note:**
- The value k is positive and will always be smaller than the length of the sorted array.
- Length of the given array is positive and will not exceed 104
- Absolute value of elements in the array and x will not exceed 104
**UPDATE (2017/9/19):**
> The arr parameter had been changed to an array of integers (instead of a list of integers). Please reload the code definition to get the latest changes.

```c++
class Solution {
public:
    vector<int> findClosestElements(vector<int>& arr, int k, int x) {
        int index=distance(arr.begin(),find(arr.begin(),arr.end(),x));
        int left=0;
        int right=arr.size()-1;
        while((right-left+1)>k)
        {
            if(abs(arr[left]-x)<=abs(arr[right]-x))//右边的大，舍弃右边的
            {
                right--;
            }
            else 
            {
                left++;
            }
        }
        right++;
        vector<int> res(&arr[left],&arr[right]);
        return res;
        
        
    }
    
};
```
