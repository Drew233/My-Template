### 最大子段和
```
#include <iostream>
using namespace std;
int main()
{
    int       n, now;
    long long maxsum, sum;

    while (cin >> n)
    {
        maxsum = sum = 0;
        for (int i = 1; i <= n; i++)
        {
            cin >> now;
            sum    = max(sum, 0LL) + now;
            maxsum = max(sum, maxsum);
        }
        cout << maxsum << endl;
    }
    return 0;
}
```
