### 编辑距离
```
#include <iostream>
#include <cstdio>
#include <cstring>
#include <algorithm>
using namespace std;
const int maxn = 1050;
int       f[maxn][maxn];
string    a, b;
bool same(char x, char y)
{
    if (x == y)
        return 0;
    return 1;
}
int main()
{
    while (cin >> a >> b)
    {
        memset(f, 0, sizeof(f)); for (int i = 0; i <= a.size(); i++)
        {
            for (int j = 0; j <= b.size(); j++)
            {
                if (i == 0)
                    f[i][j] = j;
                else if (j == 0)
                    f[i][j] = i;
                else
                    f[i][j] = min(f[i - 1][j - 1] + same(a[i - 1], b[j - 1]), min(f[i - 1][j] + 1, f[i][j - 1] + 1));
            }
        }
        cout << f[a.size()][b.size()] << endl;
    }
    return 0;
}
```
