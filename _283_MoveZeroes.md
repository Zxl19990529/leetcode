# Move Zeroes

## Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.
```
Example:

Input: [0,1,0,3,12]
Output: [1,3,12,0,0]
```
**Note:**

- You must do this in-place without making a copy of the array.
- Minimize the total number of operations.
## Code
```c++
void moveZeroes(int* nums, int numsSize) {
    int *pre = nums,*cur = nums ,*end = nums+numsSize-1;
    int i;
   while(pre<end && cur<end)
    {      
        while(pre<end && *pre!=0){
            pre++;
        }
        if(pre<end)
        {        
            cur = pre+1;
            while(cur<end && *cur==0){
                cur++;
            }
 
            *pre=*cur;
            *cur=0;  
        }
    }
}

```
