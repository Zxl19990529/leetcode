
## 重点防护 <h1>
### Description <h2>
>在战争中，物资运输和兵力运输是非常重要的，如果有一些位于重要交通线路上的城市万一落入到敌人手中，那么由于这城市的失陷，使已方控制的区域就会被分割开来，就会给自己这一方造成战争中的被动。往往这些城市都是已方重点防护或敌人重点进攻的对象。假设你就是某军的最搞指挥官，当你无论拿到已方地图或敌方地图，你能否尽快的在瞬息万变的战场形式下快速的找到要重点保护或是重点进攻的城市？

### Input <h3>
>输入有多组数据，每一组数据表示一张地图城市信息。每一组数据的第一行为一个整数Ｎ(Ｎ<=100),接着下面有m(m<=N)行描述这个地图的数据。其中每一行由多个数据组成a1,a2,…..ak组成。表示城市a1和a2,….ak有道理相连，各个数据之间用空格分开，如：输入数据5 1 2 3 4，那么表示，城市５和其它城市1,2 ,3, 4均有通路。每一组数据输入以0结束，整个输入同样以0结束。


### Output <h3>
>输出重点防护的城市个数。

Sample Input 1 
 5
 5 1 2 3 4
 0
 6
 2 1 3
 5 4 6 2
 0
 9
 2 1 3
 7 8
 5 6 4
 9 8
 0
 3
 1 2 3
 2 3
 0
 0
Sample Output 1
1
2
3
0
## 思路 <h4>
> 这道题的意思是  与城市A（只有一条路）连接的城市B是重点防护城市
>重点城市的意思是：  
>假定一个城市A
>假定一个城市B
>若A只有与B相连,而B和很多其他城市相连,那么A容易落单，B为重点城市
- 首先要创建一个二阶指针来记录城市连接情况
-其中 City[head_num][temp - 48] = 1;
- City[temp - 48][head_num] = 1;就是干这个的
- 之所以要同时x，y颠倒赋值是为了后面无论是从行检查，还是从列检查 都能保证结果是一样的
- 逐行检查，找出只有 1 个连接 的城市（行），记录其所在列 
- 用一个新数组a记录---全是0，数组的角标为之前所在列的元素赋值为1
- 数组里所有 1 的个数即为 重点防护城市 数
- 连接的城市记录为1 ，其余的地方统统初始化为0；
![](http://img.blog.csdn.net/20180311235828281)
```C++
#include<iostream>
using namespace std;
int *Links(int **city, int numsSize)   //这个函数里新增了一个数组，用来储存 哪个城市需要重点防护
{
	static int *a = new int[numsSize + 1];
	for (int i = 0; i < numsSize + 1; i++)
		a[i] = 0;
	int temp;	
	for (int i = 1; i < numsSize + 1; i++)
	{	
		int counts = 0;
		for (int j = 1; j < numsSize + 1; j++)
		{
			if (city[i][j] == 1)
			{
				counts++; 
				temp = j;
			}
		}
		if (counts > 1)
			continue;
		else
		{
			a[temp] = 1;
		}
	}
	return a;
}
int CountDangerCitys(int *link, int numsSize)  //数一下 link里新建的那个数组里需要重点保护城市的个数
{
	int counts = 0;
	for (int i = 1; i < numsSize + 1; i++)
		if (link[i] == 1)
			counts++;
	return counts;
}

int CountCitys(int numsSize)  //这里用来输入城市的信息
{
	int **City = new int*[numsSize + 1];
	for (int i = 0; i < numsSize + 1; i++)
		City[i] = new int[numsSize + 1];
	for (int i = 0; i < numsSize+1; i++)
		for (int j = 0; j < numsSize+1; j++)
			City[i][j] = 0;
	////////////////
	int head_num;
	bool Ishead = true;
	while (true)    //这个就是记录城市连接信息 的那个表
	{
		char temp;
		temp = cin.get();
		if (temp == '\n')
		{
			Ishead = true;
			continue;
		}
		if (temp > 48 && temp <= 57)
		{
			if (!Ishead)
			{
				City[head_num][temp - 48] = 1;
				City[temp - 48][head_num] = 1;
				continue;
			}
			else if (Ishead)
			{
				head_num = temp - 48;
				Ishead = false;
			}
		}
		if (temp == '0')
			break;
	}
	int *link = Links(City, numsSize);   //调用函数  往上翻
	int result = CountDangerCitys(link, numsSize);
	return result;
}

int main()
{
	int n = 1;
	int count = 0;
	//int a[100];
	//int t = 0;
	while (n != 0)
	{
		cin >> n;
		if (n != 0)count++;
		getchar();
		if (n == 0)
			break;
		int result;
		result = CountCitys(n);
		cout << result << "\n";
		//a[t] = CountCitys(n);
		//t++;
	}
	//for (int i = 0; i < count; i++)
	//	cout << a[i] << "\n";

	return 0;
}
```
