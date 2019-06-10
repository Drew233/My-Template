### 换零钱
```
#include <bits/stdc++.h>
using namespace std;
typedef long long ll;
ll solve(ll x)
{
    int coins[13]  = { 1, 2, 5, 10, 20, 50, 100, 200, 500, 1000, 2000, 5000, 10000 };
    ll  dp[100005] = { 0 };
    dp[0] = 1;
    for (int i = 0; i < 13; i++)
    {
        for (int j = coins[i]; j <= x; j++)
        {
            dp[j] = (dp[j] + dp[j - coins[i]]) % 1000000007;
        }
    }
    return dp[x];
}
int main()
{
    ll t, a;
    cin >> t;
    while (t--)
    {
        cin >> a;
        cout << solve(a) << endl;
    }
}
```
