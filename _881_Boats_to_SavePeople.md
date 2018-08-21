# Boats to Save People
## Description
> The i-th person has weight people[i], and each boat can carry a maximum weight of limit.  
> Each boat carries at most 2 people at the same time, provided the sum of the weight of those people is at most limit.  
> Return the minimum number of boats to carry every given person.  (It is guaranteed each person can be carried by a boat.)

 
```
Example 1:

Input: people = [1,2], limit = 3
Output: 1
Explanation: 1 boat (1, 2)
```
```
Example 2:

Input: people = [3,2,2,1], limit = 3
Output: 3
Explanation: 3 boats (1, 2), (2) and (3)
```
```
Example 3:

Input: people = [3,5,3,4], limit = 5
Output: 4
Explanation: 4 boats (3), (3), (4), (5)
```
**Note:**
- 1 <= people.length <= 50000
- 1 <= people[i] <= limit <= 30000

## Solution
- 如果最胖的人能和最瘦的坐一起，就坐一起，不能只能单个船拉他  
- 把人按胖瘦排好，双指针夹逼
## Code
```c++
class Solution {
public:
    int numRescueBoats(vector<int>& people, int limit) {
        sort(people.begin(), people.end());
        int i = 0, j = people.size() - 1;
        int ans = 0;

        while (i <= j) {
            ans++;
            if (people[i] + people[j] <= limit)
                i++;
            j--;
        }

        return ans;
    }
};
```