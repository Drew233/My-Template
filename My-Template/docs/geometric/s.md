### 求多边形面积
```
#include <iostream>
#include <cstdio>
#include <cstdlib>
using namespace std;
int main()
{
    int ncase;
    cin >> ncase;
    int x, y, x0, y0, sum = 0;
    cin >> x >> y;
    x0 = x;
    y0 = y;
    while (--ncase)
    {
        int xtmp, ytmp;
        cin >> xtmp >> ytmp;
        sum += (x * ytmp - y * xtmp);
        x    = xtmp;
        y    = ytmp;
    }
    sum += (x * y0 - y * x0);
    printf("%d\n", int(abs(sum) / 2));
    return 0;
}
```
