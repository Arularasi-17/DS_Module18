# Ex30 Finding Total Cost of Spanning Tree
## DATE:26.04.25
## AIM:
To write a C Program to implement Prim's Algorithm for finding Total Cost of spanning tree.
## Algorithm
1.Start with any node and mark it as part of the MST (Minimum Spanning Tree).
2.Select the smallest edge that connects a node in the MST to a node outside it.
3.Add the selected edge and the new node to the MST.
4.Repeat Step 2 until all nodes are included in the MST.
5.Sum the weights of the selected edges to get the total cost of the spanning tree.

## Program:
```
/*
Program to find and display the priority of the operator in the given Postfix expression
Developed by: ARULARASI
RegisterNumber:  212223100002
*/
#include<stdio.h>
#include<stdlib.h>
 
#define infinity 9999
#define MAX 20
 
int G[MAX][MAX],spanning[MAX][MAX],n;
 
int prims();
 
int main()
{
int i,j,total_cost;
scanf("%d",&n);
for(i=0;i<n;i++)
for(j=0;j<n;j++)
scanf("%d",&G[i][j]);
total_cost=prims();

for(i=0;i<n;i++)
{
for(j=0;j<n;j++)
printf("%d ",spanning[i][j]);
printf("\n");
}
printf("\nTotal cost of spanning tree=%d",total_cost);
return 0;
}
 
int prims()
{
int cost[MAX][MAX];
int u,v,min_distance,distance[MAX],from[MAX];
int visited[MAX],no_of_edges,i,min_cost,j;
//create cost[][] matrix,spanning[][]
for(i=0;i<n;i++)
for(j=0;j<n;j++)
{
if(G[i][j]==0)
cost[i][j]=infinity;
else
cost[i][j]=G[i][j];
spanning[i][j]=0;
}
//initialise visited[],distance[] and from[]
distance[0]=0;
visited[0]=1;
for(i=1;i<n;i++)
{
distance[i]=cost[0][i];
from[i]=0;
visited[i]=0;
}
min_cost=0; //cost of spanning tree
no_of_edges=n-1; //no. of edges to be added
while(no_of_edges>0)
{
//find the vertex at minimum distance from the tree
min_distance=infinity;
for(i=1;i<n;i++)
if(visited[i]==0&&distance[i]<min_distance)
{
v=i;
min_distance=distance[i];
}
u=from[v];
//insert the edge in spanning tree
// Text your code here
spanning[u][v]= distance[v];
spanning[v][u]= distance[v];
no_of_edges--;
visited[v]=1;
//updated the distance[] array
// Text your code here
for(i=1;i<n;i++)
if(visited[i]==0&& cost[i][v]<distance[i]){
        distance[i]= cost[i][v];
        from[i]=v;
    }
    min_cost= min_cost+cost[u][v];
}

return(min_cost);
}

```
## Output:
![image](https://github.com/user-attachments/assets/d2aafa27-00e0-4f33-b959-bc7b468fc1a5)

## Result:
Thus the C program to implement Prim's Algorithm for finding Total Cost of spanning tree is implemented successfully.
