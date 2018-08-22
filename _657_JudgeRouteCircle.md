### Judge Route Circle <h1>
### Description <h2>
> Initially, there is a Robot at position (0, 0). Given a sequence of its moves, judge if this robot makes a circle, which means it moves back to the original place.    
> The move sequence is represented by a string. And each move is represent by a character. The valid robot moves are R (Right), L  (Left), U (Up) and D (down). The output should be true or false representing whether the robot makes a circle.
```
Example 1:
Input: "UD"
Output: true
Example 2:
Input: "LL"
Output: false
```
### Code<h3>
```C++
static int __=[](){
    std::ios::sync_with_stdio(false);
    std::cin.tie(0);
    return 0;
}();
class Solution {
public:
    bool judgeCircle(string moves) {
        if(moves.length()%2!=0)return false;
        int record[18]{0};
        for(char cmd : moves)
            record[cmd-68]++;
        return ((record['D'-68]==record['U'-68]) && (record['L'-68]==record['R'-68]));
    }
};
```