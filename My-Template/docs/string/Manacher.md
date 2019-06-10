### Manacher(马拉车算法)
```
#include<bits/stdc++.h>
using namespace std;
const int MAXN = 1e5;
char str[MAXN];
char tmp[2*MAXN];
int len[2*MAXN];
int Manacher(char str[]){
	tmp[0] = '$';
	tmp[1] = '#';
	int str_len = strlen(str);
	for(int i = 1;i <= str_len;i++){
		tmp[2*i] = str[i-1];
		tmp[2*i+1] = '#';
	}
	tmp[2*str_len+2] = '\0';
	int mx = 0;
	int maxlen = -1;
	int mid;
	for(int i = 1; tmp[i]; i++){
		if(i < mx) len[i] = min(len[2*mid-i],mx-i);
		else len[i] = 1;
		while(tmp[i-len[i]] == tmp[i+len[i]]) len[i]++;
		if(len[i]+i > mx){
			mx = len[i]+i;
			mid = i;
		}
		maxlen = max(maxlen,len[i]-1);
	}
	return maxlen;//返回最长回文字串的长度
}
int main(){
	int n;
	cin>>n;
	scanf("%s",str);
	cout<<Manacher(str)；
	return 0;
}
```
