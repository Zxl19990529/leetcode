#  Uncommon Words from Two Sentences
## Description 
We are given two sentences A and B.  (A sentence is a string of space separated words.  Each word consists only of lowercase letters.)  
A word is uncommon if it appears exactly once in one of the sentences, and does not appear in the other sentence.  
Return a list of all uncommon words.   
You may return the list in any order.   
```
Example 1:

Input: A = "this apple is sweet", B = "this apple is sour"
Output: ["sweet","sour"]
```
```
Example 2:

Input: A = "apple apple", B = "banana"
Output: ["banana"]
```

**Note:**
- 0 <= A.length <= 200
- 0 <= B.length <= 200
- A and B both contain only spaces and lowercase letters.
## Solution
- 可以使用unordered_map 来储存每个单词出现的次数，只出现一次的那个肯定就是uncommon的了。
## Code
```C++
class Solution {
public:
    vector<string> uncommonFromSentences(string A, string B) {
        unordered_map<string,int> words;
        vector<string> res;
        istringstream s(A+" "+B);
        string temp;
        while(s >> temp)
        {
            words[temp]++;
        }
        for(auto word:words)
        {
            if(word.second==1)
            {
                res.push_back(word.first);
            }
        }
        return res;
    }
};
```