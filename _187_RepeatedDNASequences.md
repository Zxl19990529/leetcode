# Repeated DNA Sequences
## Description
> All DNA is composed of a series of nucleotides abbreviated as A, C, G, and T, for example: "ACGAATTCCG". When studying DNA, it is sometimes useful to identify repeated sequences within the DNA.  
Write a function to find all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule.
```c++
For example,

Given s = "AAAAACCCCCAAAAACCCCCCAAAAAGGGTTT",

Return:
["AAAAACCCCC", "CCCCCAAAAA"].
```
## Solution 
- set up an unordered_map <string,int\> to store the temp string
## Code
```C++
class Solution {
public:
    vector<string> findRepeatedDnaSequences(string s) {
        vector<string> res;
        unordered_map<string,int> map;
        for(int i=0;i<s.length();i++)
        {
            string temp_str=s.substr(i,10);
            map[temp_str]++;
        }
        for(auto it=map.begin();it!=map.end();it++)
        {
            if(it->second > 1)
                res.push_back(it->first);
        }
        return res;
    }
};
```