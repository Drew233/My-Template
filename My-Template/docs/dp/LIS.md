### 最长递增子序列
```
#include <iostream>
#include <algorithm>
#include <cstdio>
using namespace std;
const int maxn = 50050;
const int INF = 0x3f3f3f3f;
int       dp[maxn], a[maxn];
int main()
{
    int n; cin >> n; for (int i = 0; i < n; i++)
    {
        cin >> a[i];
    }
    fill(dp, dp + n, INF); for (int i = 0; i < n; i++)
    {
        *lower_bound(dp, dp + n, a[i]) = a[i];
    }
    cout << lower_bound(dp, dp + n, INF) - dp << endl;
}
```
