## 矩阵乘法<h1>
- 问题描述：
  写一个Matrix类，使得下面程序能够实现矩阵乘法
    ```C++
        #include <iostream>
        #include <cstring>
        using namespace std;

        class Matrix {
        public:
            int ** p;
        // 在此处补充你的代码
        friend ostream & operator << (ostream &o, const Matrix &a){
                for(int i = 0;i < a.r;i ++){
                    for(int j = 0;j < a.c;j ++) o << a.p[i][j] << " ";
                    o << endl;
                }
                return o;
            }
        };

        int main() {
            Matrix a, b;
            cin >> a >> b;
            cout << a * b << endl;
            return 0;
        }
    ```
    Input:
      用空行隔开的两个矩阵。矩阵第一行是行、列数。接下来是矩阵的内容。
    Output:
      一个矩阵
    Sample Input:
        ```
        3 2
        1 2
        3 4
        5 6

        2 2
        7 8
        9 0
        ```
     Sample Output:
     ```
       25 8
      57 24
      89 40
      ```
- 问题分析：
  > 对于两个矩阵相乘，得到的新矩阵的行数=第一个矩阵的行数，列数=第二个矩阵的列数。
  > 因此 在重载 * 的时候需要返回一个新对象，这个对象中的**p 行数和列数 可以通过上述法则得到
  > 此外，由于cin >> 这里输入的是对象，所以还要重载 >>  

- 解决方案：
  重载 >> 和 *
  在重载 * 中实现矩阵乘法的算法
  代码片段如下：
```C++
  // 在此处补充你的代码
	int r, c;
	Matrix() {};
	void SetMatrix(int _r, int _c)
	{
		r = _r;
		c = _c;
		p = new int*[r];
		for (int i = 0; i < r; i++)
			p[i] = new int[c];

	}
	friend istream & operator >>(istream &input,  Matrix &a)
	{
		input >> a.r >> a.c;
		a.p = new int*[a.r];
		for (int i = 0; i < a.r; i++)
			a.p[i] = new int[a.c];
		for(int i=0;i<a.r;i++)
			for (int j = 0; j < a.c; j++)
			{
				input >> a.p[i][j];
			}
		return input;
	}
	Matrix & operator *( Matrix &b)
	{
		static Matrix c;
		c.SetMatrix(this->r, b.c);
		for (int i=0;i<c.r;i++)
			for (int j = 0; j < c.c; j++)
			{
				int val = 0;
				for (int t = 0; t < this->c; t++)
					val += (this->p[i][t] * b.p[t][j]);
				c.p[i][j] = val;
			}
		return c;
	}
  ```

- 流程图+示意图（矩阵乘法的实现）：
  ![](/1.png)
  ![](/2.png)
- 结果分析：
  ![](/3.png)
  ![](/4.png)
- 总结体会：
  >这次对* 的重载不仅仅是对 运算符重载的应用，同时也需要考虑矩阵乘法算法的实现方式
  >其中用到了static ，因为在重载中临时创建的c对象在重载结束后会释放掉，所以要用static
