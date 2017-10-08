## 例11
某校决定由全校学生选举自己的学生主席。有五个候选人，编号分别为1，2，3，4，5，选举其中一人为学生会主席，每一个学生一张选票，只能填写一人。请编程完成选票工作。
### 问题分析
+ 虽然选票发放的数量一般是已知的，但收回的数量通常是无法预知的。
+ 用数组存储统计结果，而下标正好对应输入的原始信息。
### 算法设计
```c
#include<stdio.h>
int main()
{
    int i, n,a[6] = { 0 };
    printf("input data(1-5) until input -1.\n");
    scanf_s("%d", &n);
    while (n != -1)
    {
        if (n <= 5 && n >= 1)
            a[n]++;
        else
            printf("%d input error\n", n);
        scanf_s("%d", &n);
    }
    for (i = 1;i <= 5;i++)
        printf("%d number get %d notes\n", i, a[i]);
    return 0;
}
```


