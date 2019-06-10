### BFS
```
#include<iostream>
#include<algorithm>
#include<queue>
#include<cstring>
using namespace std;
#define pill pair<int,int>
int sx,sy,ex,ey,n;
char ma[1050][1050];
int vis[1050][1050];
int step[1050][1050];
int d[4][2]={-1,0,0,1,1,0,0,-1};
queue<pair<int,int> >que;
void bfs(int x,int y)
{
	vis[x][y]=1;
	que.push(pill(x,y));
	while(!que.empty())
	{
		x=que.front().first;
		y=que.front().second;
		que.pop();
		for(int i=0;i<4;i++)
		{
			int xx=x+d[i][0];
			int yy=y+d[i][1];
			if(ma[xx][yy]=='#'||xx<0||xx>=n||yy<0||yy>=n||vis[xx][yy]==1) continue;
			que.push(pill(xx,yy));
			vis[xx][yy]=1;
			step[xx][yy]=step[x][y]+1;
		}
	}
}
int main()
{
	while(cin>>n)
	{
		memset(vis,0,sizeof(vis));
		for(int i=0;i<n;i++)
		{
			scanf("%s",ma[i]);
		}
    }
}
```
