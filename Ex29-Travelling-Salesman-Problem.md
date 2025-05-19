# Ex29 Travelling Salesman Problem
## DATE:26.04.25
## AIM:
To write a C Program to implement Travelling Salesman Problem for finding shortest path.
## Algorithm
1.Start from a source city and mark it as visited.
2.Recursively visit unvisited cities, one at a time, updating the current cost.
3.Track the total cost of each possible path including the return to the starting city.
4.Use backtracking to explore all possible city orders (permutations).
5.Keep track of the minimum cost among all valid complete tours.
## Program:
```
/*
Program to implement Travelling Salesman Problem for finding shortest path
Developed by:ARULARASI 
RegisterNumber:212223100002 
*/
#include<stdio.h>
int a[10][10],com[10],n,cost=0;

// get input - no of elements , array elements , initialize array com
void input()
{
    int i,j;
    scanf("%d",&n);
    for(i=0;i<n;i++)
    {
        for(j=0;j<n;j++)
        {
            scanf("%d",&a[i][j]);
            com[i]=0;
        }
    }
}
// mincost - city 
void mincost(int city)
{
    int ncity;
    int least(int);
    
        com[city]=1;
    printf("%d--->",city+1);
    
    ncity=least(city);
    

    
    if(ncity==999)
    {
        ncity=0;
        printf("%d",ncity+1);
        cost+=a[city][ncity];
        return;
    }
    mincost(ncity);
}

// least

int least(int c)
{
    int i;
    int nc=999,min=999,kmin;
    for(i=0;i<n;i++)
    {
        if(a[c][i]!=0&&com[i]==0)
        {
            if(a[c][i]+a[i][c]<min)
            {
            min=a[i][0]+a[c][i];
            kmin=a[c][i];
            nc=i;
            }
        }
    }
    if(min!=999)
    {
        cost+=kmin;
    }
    return nc;
}

int main()
{
    input();
    mincost(0);
    printf("\n\nMinimum cost is %d\n",cost);
}
```

## Output:

![image](https://github.com/user-attachments/assets/fbba8908-d197-4b07-91ac-20b15f989150)


## Result:
Thus, the C program to implement Travelling Salesman Problem for finding shortest path is implemented successfully.
