# Dijkstra单源最短路径

## 算法描述
略
## C语言
```c
#include<stdio.h>
#include<stdlib.h>
#include<string.h>

int map[100][100];

int dijk(int v0, int vn, int n)
{
	int u0, i, j, k;
	int s[100], num, min,cur,d[100];

	memset(s, 0, sizeof(int)*100);
	s[v0] = 1;
	num = 1;
	for (i = 0; i < n; i++)
	  if (map[v0][i]!=100000)
		  d[i] = 1;
	  else
		  d[i] = 100000;

	while (num < n)
	{
		min = 100000; cur = v0;
		//找出和当前集合连接最短的点
		for (i = 1; i < n; i++)
		  for (j = 0; j < n; j++)
			{
				if (s[j] == 0 && d[j]<min)//
				{
					min = d[j];
					cur = j;
				}
			}
		s[cur] = 1;
		//更新
		for (i = 0; i < n; i++)
		{
			if (s[i] == 0 && (min + map[cur][i]) < d[i])
				d[i] = min + map[cur][i];
		}
		num++;
	}
    return d[vn]+1;
}

int main()
{
	char s1[100];
	char s[100][100];
	int len;
	int i,j,k,ch,same;


	scanf("%s", s[0]);
	scanf("%s", s1);
	len = strlen(s[0]);//字符串长度
	i = 1;
	while (scanf("%s", s[i]) != EOF)
	{
		if (strcmp(s[i],s1)!=0)//不想等
		  i++;
	}

	//i是字典长度+1
	strcpy(s[i], s1);
	i++;

	memset(map, 0, sizeof(int)*100*100);
	//计算地图
	for (j = 0; j < i;j++)
	  for (k = 0; k < i; k++)
	  {
		  if (j == k)//v0 v0
		  {
			  map[j][k] = 100000;
			  continue;
		  }
		  if (map[j][k] == 1 || map[j][k] == 100000)//计算过了
			  continue;
		  same = 0;
		  for (ch = 0; ch < len;ch++)
		    if (s[j][ch] == s[k][ch])
			  same++;
		  if (same == len - 1)
		  {
			  map[j][k] = 1;//联通
			  map[k][j] = 1;
		  }
		  else
		  {
			  map[j][k] = 100000;//不联通
			  map[k][j] = 100000;
		  }

	  }

	  printf("%d\n", dijk(0, i - 1, i));


}
```
