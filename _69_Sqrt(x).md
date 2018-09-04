#  Sqrt(x)
## Description
> Implement int sqrt(int x).  
>Compute and return the square root of x, where x is guaranteed to be a non-negative integer.  
Since the return type is an integer, the decimal digits are truncated and only the integer part of the result is returned.
```
Example 1:

Input: 4
Output: 2
```
```
Example 2:

Input: 8
Output: 2
Explanation: The square root of 8 is 2.82842..., and since 
             the decimal part is truncated, 2 is returned.
```
### Code
```c++
static const auto __ = []() {
    std::ios::sync_with_stdio(false);
    std::cin.tie(nullptr);
    return nullptr;
}();
class Solution {
public:
    int mySqrt(int x) {
        if(x==0)return 0;
        if(x==1)return 1;
        int low=0;
        int high=x;
        int mid=0;
        while(low<=high)
        {
            mid=low+(high-low)/2;
            if(mid==x/mid)
                return mid;
            else if(mid<x/mid)
                low=mid+1;
            else high=mid-1;
        }
        return mid>x/mid? mid-1:mid;
    }
};
```