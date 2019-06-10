### 快速幂
```
ll poww(ll x, ll y, ll z)
{
    ll ans = 1, base = x; while (y != 0)
    {
        if (y & 1 != 0)
            ans = ans * base % z;
        base = (base % z) * (base % z) % z; y >>= 1;
    }
    return ans;
}
```
