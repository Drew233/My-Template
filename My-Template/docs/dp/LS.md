### 最长公共子序列
```
#include <algorithm>
#include <cstdio>
#include <cstring>
#include <stack>
using namespace std;
const int maxn = 1050;
int       dp[maxn][maxn];
char      a[maxn], b[maxn];
int main()
{
    scanf("%s %s", a + 1, b + 1); int n = strlen(a + 1), m = strlen(b + 1); for (int i = 1; i <= n; i++)
        for (int j = 1; j <= m; j++)
        {
            if (a[i] == b[j])
                dp[i][j] = dp[i - 1][j - 1] + 1;
            else
                dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]);
        }
    stack<char> ans; while (n >= 1 && m >= 1)
    {
        if (dp[n][m] == 0)
            break;
        if (dp[n][m] - dp[n - 1][m - 1] == 1 && dp[n - 1][m - 1] == dp[n - 1][m] && dp[n - 1][m - 1] == dp[n][m - 1])
        {
            ans.push(a[n]); n--; m--;
        }
        else if (dp[n][m] == dp[n - 1][m] && n > 1)
            n--;
        else if (dp[n][m] == dp[n][m - 1] && m > 1)
            m--;
    }
    while (!ans.empty())
    {
        printf("%c", ans.top()); ans.pop();
    }
    puts(""); return 0;
}
```
