### 38.数数并说 <h1>
### 描述<h2>
> 报数序列是指一个整数序列，按照其中的整数的顺序进行报数，得到下一个数。其前五项如下：
```
1.     1
2.     11
3.     21
4.     1211
5.     111221
1 被读作  "one 1"  ("一个一") , 即 11。
11 被读作 "two 1s" ("两个一"）, 即 21。
21 被读作 "one 2",  "one 1" （"一个二" ,  "一个一") , 即 1211。
```
给定一个正整数 n ，输出报数序列的第 n 项。

**注意**：整数顺序将表示为一个字符串。
```
示例 1:

输入: 1
输出: "1"
示例 2:

输入: 4
输出: "1211"
```
### 分析<h2>
> 看代码，思路挺容易的
### 代码<h3>
```C++
class Solution {
public:
    string countAndSay(int n) {
        string res="";
        if(n==0)return res;
        res+="1";
        string temp="";
        string st="";
        while(--n)
        {
            int i=0;
            while(i<res.size())
           { 
                for(;res[i]==res[i+1];i++)
                {//把相同的数字摞一块
                    st+=res[i];
                }
                st+=res[i];
                temp+=to_string(st.size());
                temp+=st[0];
                st="";
                i++;
            }
            res=temp;
            temp="";
        }
        return res;
    }
};
```