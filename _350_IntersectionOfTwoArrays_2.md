### 350. 两个数组的交集 II <h1>
### 描述<h2>
> 给定两个数组，写一个方法来计算它们的交集。

**例如**:
给定 nums1 = [1, 2, 2, 1], nums2 = [2, 2], 返回 [2, 2].

**注意**：

    - 输出结果中每个元素出现的次数，应与元素在两个数组中出现的次数一致。
    - 我们可以不考虑输出结果的顺序。
### 代码<h3>
```C++
class Solution {
public:
    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
        vector<int> res;
        if(nums1.size()==0 || nums2.size()==0)return res;
        sort(nums1.begin(),nums1.end());
        sort(nums2.begin(),nums2.end());
        int id_1=0,id_2=0;
        while(id_1<nums1.size() && id_2<nums2.size())
        {
            if(nums1[id_1]==nums2[id_2])
            {
                res.push_back(nums1[id_1]);
                id_1++;id_2++;
            }
            else if(nums1[id_1]<nums2[id_2])
            {
                id_1++;
            }
            else id_2++;
        }
        return res;   
    }
};
```
