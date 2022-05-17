#include<stdio.h>
#include<string.h>

struct sut
{
	char nation[100];//国家
	int goldNumber;  //金牌数
	int silverNumber;//银牌数
	int bronzeNumber;//铜牌数
	int sum;         //总数
};
int main()
{
	struct sut a[100] = {'\0'};
	struct sut *pa = a;
	char str[9][100] = { '\0' };
	int i;
	FILE *fp = fopen("D:\\VS2015\\file.txt", "r");
	if (fp == NULL)
	{
		printf("Error\n");
		return 0;
	}
	
	while (fscanf(fp, "%s %d %d %d %d", pa->nation, &pa->goldNumber, &pa->silverNumber, &pa->bronzeNumber, &pa->sum) != EOF)
	{
		printf("%-12s%-8d%-8d%-8d%-8d\n", pa->nation, pa->goldNumber, pa->silverNumber, pa->bronzeNumber, pa->sum);
		pa++;
	}
	fclose(fp);
	
	struct sut t;
	for (i = 0; i < 8; i++)
	{
		for (int j = 0; j < 7; j++)
		{
			if (a[j].sum > a[j + 1].sum)
			{
				t = a[j];
				a[j] = a[j + 1];
				a[j + 1] = t;
			}
