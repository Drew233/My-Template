### 斐波那契(大数，根据第n项的值推出n)
```
#include <bits/stdc++.h>
using namespace std;
const int maxx = 1e9 + 7;
typedef long long ll;
ll        f[200050]; char s[100000];
int main()
{
    ios::sync_with_stdio(false);
    map<ll, ll> ma;
    f[0] = 0; f[1] = 1;
    for (ll i = 2; i < 200001; i++)
    {
        f[i]     = (f[i - 1] + f[i - 2]) % maxx;
        ma[f[i]] = i;
    }
    ll n;
    cin >> n; while (n--)
    {
        cin >> s; ll ans, num, l;
        l   = strlen(s);//先把长度求出来，用的时候直接用
        num = 0; for (ll i = 0; i < l; i++)
        {
            num = num * 10 + s[i] - '0'; num %= maxx;
        }
        cout << ma[num] << endl;
    }
    return 0;
}
```
