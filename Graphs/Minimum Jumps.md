# 2. Problem Statement:


You are given N𝑁 buildings numbered from 11 to N 𝑁 and M 𝑀 pairs of building denoting which pair of buildings are close enough to jump from one another. Given current building you are at and final building where you want to be at, find out minimum number of jumps required. If it is not possible to reach to final building, print 0.

1≤N≤35001≤𝑁≤3500

1≤M≤1061≤𝑀≤106

#### INPUT

First line contains two integers N𝑁 & M𝑀, denoting number of buildings and number of pairs of building that are close enough to jump from one another.

Next M𝑀 lines contain two integers each denoting buildings which are close enough.

Last line of input also contains two integers denoting building you are starting at and building you want to reach.

![](https://i.ibb.co/Rgstym1/final-sample.png)

#### OUTPUT

Print minimum number of jumps required to reach final building.

If it is not possible then print "00".

#### EXAMPLE

Sample 1 INPUT:  

```
5 5
1 3
2 3
1 2
3 5
4 5 
1 4
```

Sample 1 OUTPUT:  

```
3
```

Sample 2 INPUT:  

```
5 3
1 3
1 2
4 5
1 4
```

Sample 2 OUTPUT:  

```
0
```

---
```c++
#include <bits/stdc++.h>
using namespace std;


void adjList(int N, int E,vector<vector<int>>&adjL )
{
  for(int i=1;i<=E;i++)
  {
    int a,b;
    cin>>a>>b;
    adjL[a].push_back(b);
    adjL[b].push_back(a);
  }
}
void bfs(int source,vector<vector<int>>&adjL,vector<int>&dis)
{
  queue<int>q;
  dis[source]=0;
  q.push(source);
  
  while(!q.empty())
  {
    int curr=q.front();
    q.pop();
    for(int i=0;i<adjL[curr].size();i++)
      {
        int temp=adjL[curr][i];
        if(dis[temp]==-1) //not visited already
        {
          q.push(temp);
          dis[temp]=dis[curr]+1;
        }
      }
  }
  
  
}


int main() {
  
  int N,E;
  cin>>N>>E;
  vector<vector<int>>adjL(N+1);
  adjList(N,E,adjL);
  vector<int>dis(N+1,-1);
  int source,target;
  cin>>source>>target;
  
  //calculationg min dis from source to every other node using bfs
    bfs(source,adjL,dis);
    
  //printing min dis from source to target 
  if(dis[target]==-1)
  cout<<"0";
  else
  cout<<dis[target];
  

  return 0;

}

```