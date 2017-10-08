## 例12
编程统计身高（单位为厘米）。统计分150 ~ 154，155 ~ 159，160 ~ 164，165 ~ 169，170 ~ 174，175 ~ 179，低于150和高于179，共八个档次进行。
### 问题分析
由于多数统计区间的大小都固定为5，这样用“身高/5-29”做下标，则只需开辟8个元素的数组，对应8个统计档次，即可完成统计工作。
### 算法设计
```c
#include<stdio.h>
int main()
{
    int i, n, a[8] = { 0 };
    printf("input height data until input -1.\n");
    scanf_s("%d", &n);
    while (n != -1)
    {
        if (n > 179)
            a[7]++;
        else if (n < 150)
            a[0]++;
        else
            a[n / 5 - 29]++;
        scanf_s("%d", &n);
    }
    for (int i = 0;i < 8;i++) {
        switch (i)
        {
        case 0:printf("<150   ");break;
        case 1:printf("150-154");break;
        case 2:printf("155-159");break;
        case 3:printf("160-164");break;
        case 4:printf("165-169");break;
        case 5:printf("170-174");break;
        case 6:printf("175-179");break;
        case 7:printf(">179   ");break;
        }
        printf(" field the number of people: %d\n", a[i]);
    }
    return 0;
}
```
### 算法说明
算法中除了利用数学运算t=n/5-29标识了8类统计区间，还与数组下标对应，减少不必要的条件判断，提高算法效率。
