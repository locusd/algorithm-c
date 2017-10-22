### 例21
螺旋阵：任意给定n值，按如下螺旋的方式输出方阵。
n = 3 输出：
![](https://raw.githubusercontent.com/locusd/algorithm-c/master/images/example/3_21_matrix_1.PNG)
n = 4 输出：
![](https://raw.githubusercontent.com/locusd/algorithm-c/master/images/example/3_21_matrix_2.PNG)
### 问题分析1
n = 4时，可以把把矩阵最外层（1-12）当作第0层，（12-16）当作第1层，以此类推。以层作为外循环。分别计算一层左侧，下侧，右侧，上侧的数组值。
![](https://raw.githubusercontent.com/locusd/algorithm-c/master/images/example/3_21_matrix_analysis_1.PNG)

### 算法设计1
```c
#include<stdio.h>
int main()
{
    int i, j, n, a[100][100] = { 0 }, k;
    printf("input n*n matrix, n = ");
    scanf_s("%d", &n);
    k = 1;                               //计数从1开始
    for (i = 0;i < n / 2;i++)
    {
        for (j = i;j < n - i - 1;j++)    //左侧
        {
            a[j][i] = k;
            k++;
        }
        for (j = i;j < n - i - 1;j++)    //下侧
        {
            a[n - i - 1][j] = k;
            k++;
        }
        for (j = n - i - 1;j > i;j--)    //左侧
        {
            a[j][n - i - 1] = k;
            k++;
        }
        for (j = n - i - 1;j > i;j--)    //上侧
        {
            a[i][j] = k;
            k++;
        }
    }
    if (n % 2 == 1)                      //若矩阵阶数为奇数，则中央元素单独赋值为n^2
    {
        a[n / 2][n / 2] = n*n;
    }
    for (i = 0;i < n;i++)
    {
        for (j = 0;j < n;j++)
            printf("%3d ", a[i][j]);
        printf("\n");
    }
    printf("\n");
    return 0;
}
```
---
### 问题分析2(有空分析。。。)
![](https://raw.githubusercontent.com/locusd/algorithm-c/master/images/example/3_21_matrix_analysis_2.PNG)
### 算法设计2
```c
#include<stdio.h>
int main()
{
    int i, j, n, k, t, a[100][100], b[2], x, y;
    printf("input n*n matrix, n = ");
    scanf_s("%d", &n);
    b[0] = 0;
    b[1] = 1;
    k = n;
    x = 1;
    t = 1;
    while (x <= n*n) {
        for (y = 1;y <= 2 * k - 1;y++)
        {
            b[y / (k + 1)] = b[y / (k + 1)] + t;
            a[b[0]][b[1]] = x;
            x++;
        }
        k--;
        t = -t;
    }
    for (i = 1;i <= n;i++)
    {
        for (j = 1;j <= n;j++)
            printf("%3d ", a[i][j]);
        printf("\n");
    }
    printf("\n");
    return 0;
}
```