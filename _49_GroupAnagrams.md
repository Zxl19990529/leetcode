# Group Anagrams
## Description 
> Given an array of strings, group anagrams together.
```
Example:

Input: ["eat", "tea", "tan", "ate", "nat", "bat"],
Output:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]
```
**Note:**
- All inputs will be in lowercase.
- The order of your output does not matter.
## Solution
这道题一开始我想标记下每个单词中字母出现的次数，通过比较字母出现次数来分组，但是相互比较这个地方太繁琐，时间复杂度为n!  
后来看到网上答案 才想起来 unordered_map -_-|| ， unordered_map\<string\,vector\<stirng\>> 的一对多特性
## Code
```C++
static const auto _ = []()
{
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return nullptr;
}();
class Solution {
public:
    vector<vector<string> > groupAnagrams(vector<string>& strs) {
        vector< vector <string > > res;
        unordered_map < string,vector < string > > hash_map;
        for(auto t:strs)
        {
            string str=t;
            sort(str.begin(),str.end());
            hash_map[str].push_back(t);
        }
        for(auto str:hash_map)
        {
            res.push_back(str.second);
        }
        return res;
    }
};
```

## VS Code Debug
```C++
#include<iostream>
#include<vector>
#include<algorithm>
#include<string>
#include<unordered_map>
using namespace std;

class Solution {
public:
    vector<vector<string> > groupAnagrams(vector<string>& strs) {
        vector< vector <string > > res;
        unordered_map < string,vector < string > > hash_map;
        for(auto t:strs)
        {
            string str=t;
            sort(str.begin(),str.end());
            hash_map[str].push_back(t);
        }
        for(auto str:hash_map)
        {
            res.push_back(str.second);
        }
        return res;
    }
};


int main(int argc, char const *argv[])
{
     vector<string> input={"wefa","faa","aaf","asidu","sadkf","psadf","fapois","asljf"};
     Solution a;
     vector<vector<string> > t=a.groupAnagrams(input);
     for(int i=0;i<t.size();i++)
     {
         for(int j=0;j<t[i].size();j++)
         {
             string str= t[i][j];
             cout << str <<" ";
         }
         cout << "\n" ;
     }
    return 0;
}

```