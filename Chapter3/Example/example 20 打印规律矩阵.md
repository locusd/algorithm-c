### 例20
编程打印如下规律的n*n方阵  
使左对角线和右对角线上的元素为0，它们上方元素为1，左方元素为2，下方元素为3，右方元素为4，下方是一个符合条件的五阶矩阵。  
![](https://raw.githubusercontent.com/locusd/algorithm-c/master/images/example/3_20_matrix.PNG)

### 算法设计1
```c
#include<stdio.h>
int main()
{
    int i, j, n, a[100][100] = { 0 };
    printf("input n*n matrix, n = ");
    scanf_s("%d", &n);
    for (i = 0;i < n;i++)
        for (j = 0;j < n;j++)
        {
            if (i == j || i + j == n - 1) a[i][j] = 0;
            else if (i < j && i + j < n - 1) a[i][j] = 1;
            else if (i > j && i + j < n - 1) a[i][j] = 2;
            else if (i > j && i + j > n - 1) a[i][j] = 3;
            else if (i < j && i + j > n - 1) a[i][j] = 4;
        }
    for (i = 0;i < n;i++) {
        for (j = 0;j < n;j++)
        {
            printf("%d ", a[i][j]);
        }
        printf("\n");
    }
    printf("\n");
    return 0;
}
```