# Minimum Time Difference

## Description

> Given a list of 24-hour clock time points in "Hour:Minutes" format, find the minimum minutes difference between any two time points in the list.

```R
Example 1:
Input: ["23:59","00:00"]
Output: 1
```

**Note:**

- The number of time points in the given list is at least 2 and won't exceed 20000.
- The input time is legal and ranges from 00:00 to 23:59.

## Codes

```C++
class Solution {
public:
    int findMinDifference(vector<string>& timePoints) {
        int minDif = 24 * 60;
        sort(timePoints.begin(),timePoints.end());// 先小后大
        for (int i = 0; i < timePoints.size(); i++)
        {
            string a = timePoints[i], b = timePoints[(i + 1) % timePoints.size()];// 最晚的时间和最早的时间比较
            stringstream sa(a), sb(b);
            int h1, m1, h2, m2;
            char c;
            sa >> h1 >> c >> m1;
            sb >> h2 >> c >> m2;
            int dif = (h2 - h1) * 60 + (m2 - m1);
            if (i == timePoints.size() - 1)// 比较到最后一个了
                dif += 24 * 60;
            minDif = min(minDif, dif);
        }
        return minDif;
    }
   
};
```