### DFS(不知道这个板子该怎么找，先这样吧)
```
#include <stdio.h>
#include <stdlib.h>
int book[10], a[10], n;

void dfs(int step)
{
    int i;
    if (step == n + 1)//当你在第n+1步的时候，说明前n部已经排好了。
    {
        for (i = 1; i <= n; i++)
            printf("%d ", a[i]);
        printf("\n");

        return; //返回之前的一步；
    }

    for (i = 1; i <= n; i++) //按照1，2，3.。。的方式一一尝试。
    {
        if (book[i] == 0)    //判断扑克牌i是不是还在手里
        {
            a[step] = i;     //将i牌放在第step个盒子里。
            book[i] = 1;     //表示扑克牌不再第step个盒子里
            dfs(step + 1);   //继续下一步。
            book[i] = 0;     //将刚才尝试的扑克收回，才能进行下一步的尝试。
        }
    }
    return; //结束搜索。
}
int main()
{
    while (~scanf("%d", &n))
        dfs(1);

    return 0;
}

```
