## 例4
编写算法：打印具有以下规律的图形

&ensp;1 

&ensp;5&emsp;2

&ensp;8&emsp;6&emsp;3

10&emsp;9&emsp;7&emsp;4
### 算法分析
将图中1，2，3，4所在位置称为第一层（主对脚线），而5，6，7称为第二层，依次类推。<br>
以层号为外循环，循环变量为i（范围为1 ~ n）<br>
以层内元素从左上到右下的序号为内循环，循环变量为j（范围为1 ~ n+1-i）<br>
则，i 层第 j 个数据对应的数组元素为a[ i - 1 + j ][ j ]。<br>
### 算法设计
```c
#include<stdio.h>
int main()
{
    int i, j, a[100][100], n, k;
    printf("输入n*n数组的n值： ");
    scanf_s("%d", &n);
    for (i = 0;i < n;i++)              //初始化n*n数组元素为0；
        for (j = 0;j < n;j++)
            a[i][j] = 0;
    k = 1;
    for (i = 1;i <= n;i++)             //开始为 i 层第 j 元素赋值
        for (j = 1;j <= n + 1 - i;j++)
        {
            a[i + j - 2][j - 1] = k;   //由于c语言数组从a[0][0]开始，所以要各减一
            k++;
        }
    for (i = 0;i < n;i++)              //输出数组，若元素为零，则忽略
    {
        for (j = 0;j < n;j++)
            if (a[i][j] != 0)
                printf("%6d", a[i][j]);
        printf("\n");
    }
    return 0;
}
```


