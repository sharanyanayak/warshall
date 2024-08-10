(warshall)
#include<stdio.h>
#define MAX 10
int D[MAX][MAX],n;
void warshall()
{
int i,j,k;
for(k=1;k<=n;k++)
for(i=1;i<=n;i++)
for(j=1;j<=n;j++)
D[i][j] = D[i][j] || ( D[i][k] && D[k][j] );
}
void main()
{
int i, j;
printf("Enter the number of vertices :\n");
scanf("%d",&n);
printf("Enter the adjacency matrix\n");
for(i=1;i<=n;i++)
for( j=1;j<=n;j++)
scanf("%d",&D[i][j]);
warshall();
printf("Trasitive closure of digraph is :\n");
for( i=1;i<=n;i++)
{
for( j=1;j<=n;j++)
printf("%d\t",D[i][j]);
printf("\n") ;
}
}
(floyd)
#include<stdio.h>
#include <stdlib.h>
#define MAX 10
#define min(c,d) (c<d?c:d)
int dist[MAX][MAX],n;
void floyd()
{
int i,j,k;
for(k=1;k<=n;k++) // record the lengths of shortest path
for(i=1;i<=n;i++)
for(j=1;j<=n;j++)
dist[i][j]=min(dist[i][j],dist[i][k]+dist[k][j]);
}
void main()
{
int i, j;
printf("Enter the number of vertices :\n");
scanf("%d",&n);
printf("Enter the distance matrix\n");//read distance matrix
for(i=1;i<=n;i++)
for( j=1;j<=n;j++)
scanf("%d",&dist[i][j]);
floyd();
printf("\nAll pairs shortest path matrix is :\n");
for( i=1;i<=n;i++)
{
for( j=1;j<=n;j++)
{
printf("%d\t",dist[i][j]);
}
printf("\n");
}
}
