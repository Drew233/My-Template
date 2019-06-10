### 大数相加(正整数)
```
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;
int main()
{
    int n;
    cin >> n;
    int m = 0;
    int l = 0;
    for (int i = 1; i <= n; i++)
    {
        string s1, s2, s(10000, '0');
        cin >> s1 >> s2;
        m++;
        cout << (l++ ? "\n" : "");
        reverse(s1.begin(), s1.end());
        reverse(s2.begin(), s2.end());
        for (int j = 0; j < s1.length(); j++)
            s[j] = s1[j];
        int temp = 0;
        for (int k = 0; k < s2.length(); k++)
        {
            temp += s[k] - 48 + s2[k] - 48;
            s[k]  = temp % 10 + '0';
            temp /= 10;
        }
        s[s2.length()] = s[s2.length()] - 48 + temp + 48;
        reverse(s.begin(), s.end());
        reverse(s1.begin(), s1.end());
        reverse(s2.begin(), s2.end());
        cout << "Case" << m << ":" << endl;
        cout << s1 << "+" << s2 << "=" << s.substr(s.find_first_not_of('0')) << endl;
    }
    return 0;
}
```
### 大数相减(正整数)
```
#include <iostream>
#include <string>
#include <cstring>
#include <vector>
#include <algorithm>
using namespace std;
int strComp(string &s1, string &s2)
{
    int len1 = s1.length();
    int len2 = s2.length();
    if (len1 > len2)
        return 0;
    else if (len1 < len2)
        return 1;
    else
    {
        if (s1 >= s2)
            return 0;
        else
            return 1;
    }
}
int main()
{
    string s1, s2;
    while (cin >> s1 >> s2)
    {
        string s(10000, '0');
        bool   fgEx = true;
        if (strComp(s1, s2) == 1)
        {
            string temp;
            temp = s1;
            s1   = s2;
            s2   = temp;
            fgEx = false;
        }
        if (s1 == s2)
        {
            cout << s1 << " - " << s2 << " = " << "0" << endl;
            continue;
        }
        reverse(s1.begin(), s1.end());
        reverse(s2.begin(), s2.end());
        for (int i = 0; i < s1.length(); i++)
            s[i] = s1[i];
        for (int i = 0; i < s2.length(); i++)
        {
            if (s[i] >= s2[i])
                s[i] = s[i] - '0' - (s2[i] - '0') + '0';
            else
            {
                s[i + 1] = s[i + 1] - '0' - 1 + '0';
                s[i]     = s[i] - '0' + 10 - (s2[i] - '0') + '0';
            }
        }
        if (fgEx == false)
        {
            reverse(s2.begin(), s2.end());
            cout << s2 << " - ";
            reverse(s1.begin(), s1.end());
            cout << s1 << " = ";
            reverse(s.begin(), s.end());
            cout << "-" << s.substr(s.find_first_not_of('0')) << endl;
        }
        else
        {
            reverse(s1.begin(), s1.end());
            cout << s1 << " - ";
            reverse(s2.begin(), s2.end());
            cout << s2 << " = ";
            reverse(s.begin(), s.end());
            cout << s.substr(s.find_first_not_of('0')) << endl;
        }
    }
    return 0;
}
```
### 大数相乘(正整数)
```
#include <iostream>
#include <string>
#include <cstring>
#include <vector>
#include <algorithm>
using namespace std;
int main()
{
    string s1, s2;
    while (cin >> s1 >> s2)
    {
        string s(1000, '0');
        reverse(s1.begin(), s1.end());
        reverse(s2.begin(), s2.end());
        for (int i = 0; i < s1.length(); i++)
            for (int j = 0; j < s2.length(); j++)
            {
                int temp = (s1[i] - '0') * (s2[j] - '0');
                s[i + j + 1] = s[i + j + 1] - '0' + (s[i + j] - '0' + temp) / 10 + '0';
                s[i + j]     = (s[i + j] - '0' + temp) % 10 + '0';
            }
        reverse(s.begin(), s.end());
        if (s.find_first_not_of('0') == string::npos)
            cout << "0" << endl;
        else
            cout << s.substr(s.find_first_not_of('0')) << endl;
    }
    return 0;
}
```
### 大数相除(正整数)
```
#include <iostream>
#include <string>
#include <cstring>
#include <vector>
#include <algorithm>
using namespace std;
int strComp(string &s1, string &s2)
{
    int len1 = s1.length();
    int len2 = s2.length();
    if (len1 > len2)
        return 0;
    else if (len1 < len2)
        return 1;
    else
    {
        if (s1 >= s2)
            return 0;
        else
            return 1;
    }
}
string Sub(string s1, string s2)
{
    if (strComp(s1, s2) == 1)
        return "-1";
    reverse(s1.begin(), s1.end());
    reverse(s2.begin(), s2.end());
    string s(1000, '0');
    for (int i = 0; i < s1.length(); i++)
        s[i] = s1[i];
    for (int i = 0; i < s2.length(); i++)
    {
        if (s[i] >= s2[i])
            s[i] = s[i] - '0' - (s2[i] - '0') + '0';
        else
        {
            s[i + 1] = s[i + 1] - '0' - 1 + '0';
            s[i]     = s[i] - '0' + 10 - (s2[i] - '0') + '0';
        }
    }
    reverse(s.begin(), s.end());
    if (s.find_first_not_of('0') == string::npos)
        return "0";
    else
        return s.substr(s.find_first_not_of('0'));
}
int main()
{
    string s1, s2;
    while (cin >> s1 >> s2)
    {
        string s(1000, '0');
        if (strComp(s1, s2) == 1)
        {
            cout << "0" << endl;
            continue;
        }
        int len1 = s1.length();
        int len2 = s2.length();
        int dis  = len1 - len2;
        for (int i = 0; i < dis; i++)
            s2 += '0';
        string ans(1000, '0');
        while (dis >= 0)
        {
            int    sum = 0;
            string temp;
            while ((temp = Sub(s1, s2)) != "-1")
            {
                sum++;
                s1 = temp;
            }
            ans[ans.length() - dis - 1] = sum + '0';
            dis--;
            s2 = s2.substr(0, len2 + dis);
        }
        if (ans.find_first_not_of('0') == string::npos)
            cout << "0" << endl;
        else
        {
            string res = ans.substr(ans.find_first_not_of('0'));
            cout << res << endl;
        }
    }
    return 0;
}
```
### 大数取模
```
typedef long long ll;
cin >> s;
ll ans, num;
ll l = strlen(s);
num = 0;
for (ll i = 0; i < l; i++)
{
    num = num * 10 + s[i] - '0';
    num %= maxx;
}               
```
