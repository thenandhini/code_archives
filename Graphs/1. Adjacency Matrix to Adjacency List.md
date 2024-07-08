# 1.Problem Statement:
You will be given a graph with N nodes represented as an Adjacency matrix. Convert it into its equivalent Adjacency list and print in the format as given in the output section. As a refresher, in a Adjacency Matrix M𝑀, Mij𝑀𝑖𝑗 represents 1 iff there exists an edge between ith & jth node.

1≤N≤1001≤𝑁≤100

0≤Mij≤10≤𝑀𝑖𝑗≤1

#### INPUT

First line contains an integer N 𝑁, representing size of a square matrix.

Next N𝑁 lines contain N 𝑁 integer each representing the given Adjacency Matrix.

#### OUTPUT

Print N𝑁 lines. ith 𝑖𝑡ℎ line begins with "i: " prefix followed by all nodes that share an edge with ith 𝑖𝑡ℎ node separated by space. See sample for clarity.

#### EXAMPLE

Sample 1 INPUT:  

```
4
0 1 0 1
1 0 1 0
0 1 1 1
1 0 1 1
```

Sample 1 OUTPUT:  

```
1: 2 4 
2: 1 3 
3: 2 3 4 
4: 1 3 4 
```

---
# Code

```C++

#include<iostream>
#include<vector>
using namespace std;



void adjList(vector<vector<int>>&adjMat,int N)
{
  //conversion into adjList
 
  vector<vector<int>>adjList(N+1);
  for(int i=1;i<=N;i++)
    {
     for(int j=1;j<=N;j++)
        {
        if(adjMat[i][j]==1)
        adjList[i].push_back(j);
      
         
        }
    }
 
  //print the converted adjList
  for(int i=1;i<=N;i++)
  {
    cout<<i<<":"<<" ";
    for(int j=0;j<adjList[i].size();j++)
    {
      cout<<adjList[i][j]<<" ";
    
    }
    cout<<endl;
  }
  
}




int main() {
  int N;
  cin>>N;
  vector<vector<int>>adjMat(N+1,vector<int>(N+1,0));
  for(int i=1;i<=N;i++)
  {
    for(int j=1;j<=N;j++)
    {
      cin>>adjMat[i][j];
    }
    
  }
  
  adjList(adjMat,N);
 
}
```
