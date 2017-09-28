## 例1 交换i和j的内容
```c
#include<stdio.h>
void swap(int *i, int *j);
int main()
{
	int i, j;
	printf("输入i, j:");
	scanf_s("%d %d", &i, &j);
	printf("i = %d, j = %d\n", i, j);
	printf("交换i, j后");
	swap(&i, &j);
	printf("输出i, j\ni = %d, j = %d\n", i, j);
	return 0;
}
void swap(int *i, int *j){
 	int temp;
	temp = *i;
	*i = *j;
	*j = temp;
}
 ```
