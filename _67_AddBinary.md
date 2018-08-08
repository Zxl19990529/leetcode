### Add Binary <h1>
### Description <h2>

> Given two binary strings, return their sum (also a binary string).

> The input strings are both non-empty and contains only characters 1 or 0.
```
Example 1:

Input: a = "11", b = "1"
Output: "100"
```
```
Example 2:

Input: a = "1010", b = "1011"
Output: "10101"
```
### Code<h3>

```C++
class Solution {
public:
    int carry=0;
    int temp;
    string addBinary(string a, string b) {
        string res="";
        int len_max=max(a.length(),b.length());
        for(int i=0;i<len_max;i++)
        {
            int temp_a= (i<a.length()? a[a.length()-i-1]-48:0);
            int temp_b= (i<b.length()? b[b.length()-i-1]-48:0);
            temp=(temp_a+temp_b+carry)%2;
            carry=(temp_a+temp_b+carry)/2;
            res.insert(res.begin(),temp+48);
        }
        return carry==0 ? res:"1"+res;        
    }
};
```

