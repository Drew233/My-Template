### Eratosthenes(埃拉托色尼筛法)
```
#include<bits/stdc++.h>
using namespace std;
int a[1000000];
int main()
{
	int sum=0,n;
	int i,j;
	while(~scanf("%d",&n))
	{
		sum=0;
		for(i=2;i<=n;i++)
     	a[i]=1;
 		for(i=2;i<=sqrt(n);i++){
  		for(j=2*i;j<=n;j+=i){
   			a[j]=0;
  			}
 		}
	 	for(i=2;i<=n;i++){
	  	if(a[i])
		cout<<i<<endl;;
	 	}
	}
 return 0;
}
```
### 欧拉筛
```
#include<stdio.h>
#include<stdbool.h>
#define N 100
int main(void)
{
    bool number[N+1];
    int prime[N+1];
    int i,j,count=0;
    memset(number,true,sizeof(number));
    for(i=2;i<=N;i++)
    {
        if(number[i])
            prime[count++]=i;
        for(j=0;j<count&&prime[j]*i<=N;j++)
        {
            number[prime[j]*i]=false;
            if(i%prime[j]==0)//精华就在于此：它保证每个合数只会被它的最小质因数筛去，因此每个数只会被标记一次，所以时间复杂度是O(n)
                break;
        }
    }
    for(i=2;i<N+1;i++)
        if(number[i]==true)
            printf("%d ",i);
    return 0;
}
```
