### kruskal
```
#include <bits/stdc++.h>
using namespace std;
struct city
{
    int a;
    int b;
    int p;
}   c[105];
int p[105];
int find(int x)
{
    return p[x] != x ? p[x] = find(p[x]) : x;
}
void join(int x, int y)
{
    x = find(x);
    y = find(y);
    if (x != y)
        p[y] = x;
}
bool cmp(city x, city y)
{
    return x.p < y.p;
}
int main()
{
    int n, m;
    while (cin >> n >> m)
    {
        int sum = 0;
        if (n == 0)
            break;
        for (int i = 1; i <= m; i++)
            p[i] = i;
        for (int i = 0; i < n; i++)
            cin >> c[i].a >> c[i].b >> c[i].p;
        sort(c, c + n, cmp);
        for (int i = 0; i < n; i++)
        {
            if (find(c[i].a) != find(c[i].b))
            {
                join(c[i].a, c[i].b);
                sum += c[i].p;
            }
        }
        int flag = 0;
        for (int i = 1; i <= m; i++)
        {
            if (p[i] == i)
                flag++;
        }
        if (flag == 1)
            cout << sum << endl;
        else
            puts("?");
    }
    return 0;
}
```
