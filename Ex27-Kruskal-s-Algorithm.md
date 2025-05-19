# Ex27 Kruskal’s Algorithm
## DATE:24.04.2025
## AIM:
To write a C program to implement Kruskal's Algorithm for finding minimum cost
## Algorithm
1. Input the number of vertices and the cost adjacency matrix
2. Initialize the minimum cost to 0 and create a parent[] array for the union-find structure.
3. Repeat until (n - 1) edges are included in the MST
4. Check for cycles using union-find: 
5. Mark the edge as used by setting its cost to 999 in both directions and print the MST edges with the total minimum cost.
## Program:
```
/*
Program to implement Kruskal's Algorithm
Developed by: ARULARASI
RegisterNumber:  212223100002
*/

    #include <stdio.h>
    #include <stdlib.h>
    int i,j,k,a,b,u,v,n,ne=1;
    int min,mincost=0,cost[9][9],parent[9];
    int find(int);
    int uni(int,int);
    int main()
    {
          scanf("%d",&n);
          for(i=1;i<=n;i++)
     {
     for(j=1;j<=n;j++)
     {
     scanf("%d",&cost[i][j]);
     if(cost[i][j]==0)
     cost[i][j]=999;
     }
     }
         while(ne < n)
     {
     for(i=1,min=999;i<=n;i++)
     {
     for(j=1;j <= n;j++)
     {
     if(cost[i][j] < min)
     {
     min=cost[i][j];
     a=u=i;
     b=v=j;
     }
     }
     }
     u=find(u);
     v=find(v);
     if(uni(u,v))
     {
     printf("%d edge (%d,%d) =%d\n",ne++,a,b,min);
     mincost +=min;
     }
     cost[a][b]=cost[b][a]=999;
     }
     printf("Minimum cost = %d\n",mincost);
     return 0;
       }
    
    // Text your code here for find() and uni()
    int find(int i){
        while(parent[i])
            i=parent[i];
        return i;
    }
    int uni(int i,int j){
        if(i!=j){
            parent[j]=i;
            return 1;
        
    }
     return 0;
    }
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/4324c2a8-90cc-49a0-b30e-fc2f1d4401b0)
## Result:
Thus, the C program to implement Kruskal's Algorithm for finding minimum cost is implemented successfully.
