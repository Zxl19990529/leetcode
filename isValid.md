### 有效括号<h1>
### 描述<h2>
> 给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。  
> 有效字符串需满足：  

- 左括号必须用相同类型的右括号闭合。
- 左括号必须以正确的顺序闭合。
- 注意空字符串可被认为是有效字符串。

- 示例 1:
```
输入: "()"
输出: true
```
- 示例 2:
```
输入: "()[]{}"
输出: true
```
- 示例 3:
```
输入: "(]"
输出: false
```
- 示例 4:
```
输入: "([)]"
输出: false
```
- 示例 5:
```
输入: "{[]}"
输出: true
```
### 思路<h4>
- 以前C的时候用的是 数组遍历，每次找到括号就在对应的下面标0记录
- 用栈做，把每次遇到的左括号压进栈
- 用栈顶检查是否为匹配的右括号
- 遇到匹配就pop
- 最后如果栈不空，则说明有括号落单了
### 代码<h5>
```C++
class Solution {
public:
    bool isValid(string s) {
        if (s.size() % 2)return false;
	stack <char> st;
	for (int i = 0; i < s.size(); i++)
	{
		char temp = s[i];
		switch (temp)
		{
		case '(':st.push(temp); break;
		case'[':st.push(temp); break;
		case'{':st.push(temp); break;
		default:
			break;
		}
		if (!st.empty())
		{
			bool judge = match(st.top(), temp);
			if (judge)
				st.pop();
		}
	}
	return st.empty() ? true : false;
    }
    bool match(char a, char b)
{
	if (a == '('&&b == ')')return true;
	if (a == '['&&b == ']')return true;
	if (a == '{'&&b == '}')return true;
	return false;
}
};
```
