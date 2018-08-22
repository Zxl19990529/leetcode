###  Excel Sheet Column Number 
### Description 
> Given a column title as appear in an Excel sheet, return its corresponding column number.
```
For example:

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...
```
```
Example 1:
Input: "A"
Output: 1

Example 2:
Input: "AB"
Output: 28

Example 3:
Input: "ZY"
Output: 701
```
### Code
```C++
class Solution {
public:
    int titleToNumber(string s) {
        int len=s.length();
        int index=0;
        for(int i=0;i<len;i++)
        {
            index+=(s[len-i-1]-64)*pow(26,i);
        }
        return index;
    }
};
```