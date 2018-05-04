### 寻找重复数<h1>
### 描述<h2>
> 一个长度为 n + 1 的整形数组，其中的数字都在 1 到 n 之间，包括 1 和 n ，可知至少有一个重复的数字存在。  
> 假设只有一个数字重复，找出这个重复的数字。
### 注意<h3>
- 不能更改数组内容（假设数组是只读的）。
- 只能使用恒定的额外空间，即要求空间复杂度是 O(1) 。
- 时间复杂度小于 O(n2)
- 数组中只有一个数字重复，但它可能不止一次重复出现。
### 思路<h4>
- STL大法好
- set 的时间复杂度为O(Log n)
### 代码<h5>
```C++
static auto x = [](){
    std::ios::sync_with_stdio(false);
    std::cin.tie(NULL);
    return 0;
}();
class Solution {
public:
    int findDuplicate(vector<int>& nums) {
        multiset<int> temp(nums.begin(), nums.end());
		//multiset<int>::iterator it;
		for (int i = 0; i < nums.size(); i++)
		{
			int flag = temp.count(nums[i]);
			if (flag > 1)
				return nums[i];
		}
    }
};
```
