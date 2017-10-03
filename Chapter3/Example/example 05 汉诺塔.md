## 例5
汉诺塔问题，把n个盘子（大的在下，小的在上，从上到下盘子编号分别为1，2，...，n）从A基座移动到B基座，C为辅助基座，移动过程三个基座上的盘子始终保持大的在上，小的在下。请编程打印出移动过程。

### 算法分析
利用递归把大规模问题转化为小规模问题<br>
第一步：先把A基座上n-1个盘子看作整体移动到C基座上<br>
第二步：再把A基座上第n个盘子移动到B基座上<br>
第三步：最后把C基座上n-1个盘子移动到B基座上<br>
### 算法设计
```c
#include<stdio.h>
void hanoi(char a, char b, char c, int n);
int main()
{
    int n;
    printf("输入n阶汉诺塔的n值：");
    scanf_s("%d", &n);
    hanoi('A', 'B', 'C', n);
    return 0;
}
void hanoi(char a, char b, char c, int n)  //第一个参数a代表每次移动的起始基座
{                                          //第二个参数b代表每次移动的终点基座
    if (n > 0) {                           //第三个参数c代表每次移动的辅助基座
        hanoi(a, c, b, n - 1);             //第四个参数n代表所要移动的盘子编号
        printf("Move dish %d from pile %c to %c\n", n, a, b);
        hanoi(c, b, a, n - 1);
    }
}
```


