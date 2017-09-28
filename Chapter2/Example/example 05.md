## 例5 在一组数据中查找给定值 k（数据存储在数组a[0..n-1]中）
```c
#include<stdio.h>
int main()
{
    int i, k, a[10];
    for(i = 0;i < 10;i++)
    {
        a[i] = i + 1;
    }
    printf("输入k值(1-10)：");
    scanf_s("%d", &k);
    i = 0;
    while(i < 10 && a[i] != k)
    {
        i++;
    }
    if(i < 10) printf("k值放在数组a的第%d元素上",i + 1);
    else printf("k 不在数组a上");
    return 0; 
}
```
