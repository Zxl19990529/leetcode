
## 题目描述 <h1>
>编写一个高效的算法来搜索 m x n 矩阵中的一个目标值。该矩阵具有以下特性：
- 每行中的整数从左到右排序。
- 每行的第一个整数大于前一行的最后一个整数。
## 示例：<h2>
>以下矩阵：
```C
[
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50],
]
给出 target = 3，返回 true
```


## 思路： <h3>
- 如果该数字大于target，那么该数字所在的列就可以排除;
- 如果该数字小于target，那么该数字所在的行就可以排除;

代码如下：

# 解法1：时间复杂度位O(N^2) <h5>
```C
    
     boolean flag = false;
     public boolean searchMatrix(int[][] matrix, int target) {
         // write your code here
         for(int i = 0; i<=matrix.length-1;i++){
             for(int j = 0 ; j<=matrix[i].length-1;j++){
                 if(matrix[i][j]==target){
                     flag=true;
                     break;
                 }
             }
         }
         return flag;
     }

   
 ```
# 解法2： <h4>
```C
    
    boolean flag = false;
    public boolean searchMatrix(int[][] matrix,int target){
        int rows = matrix.length;//二维数组的行数
        int columns=0;//初始化二维数组的列数
        if(rows==0){//二维数组里行数为0
            columns=0;//列数为0
        }else{
            columns = matrix[0].length;
        }
        int row=0;//元素的位置（横坐标）
        int column = columns-1;//元素的位置（纵坐标）
        if(matrix!=null && rows>0 && columns>0){//二维数组存在且里边有元素
            while( row < rows && column >= 0 ) {
                if(matrix[row][column] == target){//如果矩阵右上角的元素就是要找的元素
                    flag = true;
                    break;
                }else if(matrix[row][column] < target ){//矩阵右上角的元素小于要找的元素
                    ++row;//排除matrix[row][column]所在的行
                }else {
                    --column;//排除matrix[row][column]所在的列
                }
            }
        }else{
            flag = false;
        }
        return flag;
    }
```
