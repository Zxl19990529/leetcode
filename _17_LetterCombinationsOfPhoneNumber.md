### LetterCombinationsOfPhoneNumber <h1>
### Description <h2>
> Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent.  
> A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.
![](http://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)
```
Example:

Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```
**Note**  
Although the above answer is in lexicographical order, your answer could be in any order you want.
### 分析<h3>
> 以往组合的前提是给定个数，但是这道题的变量是string  
> 那么组合的时候每次需要组合的 列向量 都会增加  
> 这里可以用temp来复制res 进行变化，然后在把temp 复制回去  
> 对于数字字母组合，可以用一个map来储存 
### 代码<h4>
```C++
class Solution {
public:
    vector<string> letterCombinations(string digits) {
       	vector<string> res;
	if (digits.size() == 0)return res;
	res.push_back("");
	map<char, string> mp = { { '1',"" },{ '2',"abc" },{ '3',"def" },{ '4',"ghi" },{ '5',"jkl" },{ '6',"mno" },{ '7',"pqrs" },{ '8',"tuv" },{ '9',"wxyz" } };
	for (int i = 0; i<digits.size(); i++)
	{
        if (digits[i] == '1')continue;
		vector<string> temp;
        
		for (int j = 0; j<res.size(); j++)
		{//每次需要被组合的列向量都在变化
			auto p = mp.find(digits[i]);
			for (int k = 0; k<p->second.size(); k++)
			{
				temp.push_back(res[j] + p->second[k]);
			}
		}
		res.assign(temp.begin(), temp.end());
	}
	return res;
    }
};
```