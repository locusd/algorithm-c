## 例1 求下列公式
![](https://raw.githubusercontent.com/locusd/algorithm-c/master/images/example/3_1_formula.PNG)

### 数学模型1
![](https://raw.githubusercontent.com/locusd/algorithm-c/master/images/example/3_1_model.PNG)
### 算法设计1
```c
#include<stdio.h>
int main()
{
	int i, j, n, sign;
	float sum, frac;
	printf("输入n值： ");
	scanf_s("%d", &n);
	sum = 0;
	for (i = 1; i <= n; i++)
	{
		frac = 1;                   //求阶乘
		for (j = 1; j <= 2 * i - 1; j++)
		{
			frac = frac * j;
		}
		sign = 1;
		for (j = 1; j <= i + 1; j++)  //求正负
		{
			sign = sign * (-1);
		}
		sum = sum + sign / frac;
	}
	printf("当n = %d时，公式结果为：%f\n", n, sum);
}
```
