#  Valid Anagram
## Description
> Given two strings s and t , write a function to determine if t is an anagram of s.
```ruby
Example 1:
Input: s = "anagram", t = "nagaram"
Output: true

Example 2:
Input: s = "rat", t = "car"
Output: false
```
**Note:**
- You may assume the string contains only lowercase alphabets.
Follow up:
- What if the inputs contain unicode characters? How would you adapt your solution to such case?

## Code
```C++
static auto x = []() {
    ios::sync_with_stdio(false);
    cin.tie(nullptr);
    return 0;
}();
class Solution {
public:
    bool isAnagram(string s, string t) {
        if(s.size()!=t.size())return false;        
        int s_[128]{0};
        int t_[128]{0};
        for(char i:s)s_[i]++;
        for(char i:t)t_[i]++;
        for(int i='a';i<='z';i++)
            if (s_[i]!=t_[i])
                return false;
        return true;
    }
};
```


