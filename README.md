# FD
#include<stdio.h>

#include<conio.h>

#include<math.h>

void main()

{

	int i,j,n,m[100];
	float BP[100],AP[100],FRBP[100],FRAP[100],Spread[100];

clrscr();

	printf("Enter Spot Rate Bid Price :\t");

	scanf("%f",&BP[0]);

	printf("Enter Spot Rate Ask Price :\t");

	scanf("%f",&AP[0]);	



	printf("How many Forward Rate Maturity Periods you Wanna Enter : \t");

	scanf("%d",&n);

	printf("Enter %d Forward Rates Maturity Months ",n);

	for(i=1;i<=n;i++)

	{

		scanf("%d", &m[i]);

	}





	for(i=1;i<=n;i++)

	{

	printf("Enter %d Month FRBP :\t",m[i]);

	scanf("%f",&FRBP[i]);

	

	printf("Enter %d Month FRAP :\t",m[i]);

	scanf("%f",&FRAP[i]);

	}



	for(i=1;i<=n;i++)

	{

		if(FRBP[i]>FRAP[i])

		{

			BP[i]=BP[0]-(FRBP[i]/10000);

			AP[i]=AP[0]-(FRAP[i]/10000);

		}

		else

		{

			BP[i]=BP[0]+(FRBP[i]/10000);

			AP[i]=AP[0]+(FRAP[i]/10000);

		}

	}



	for(i=0;i<=n;i++)

	{

		Spread[i]=AP[i]-BP[i];

	}





	printf("Maturity \t Bid Price\t Ask Price\t Spread");



	for(i=0;i<=n;i++)

	{

		if(i==0)

		{

			printf("Spot Rate \t %f\t%f\t%f",BP[i],AP[i],Spread[i]);

		}

		else

		{

			printf(" %d\t\t %f\t%f\t%f",m[i],BP[i],AP[i],Spread[i]);

		}

	}



	printf("Premium (or) Discount Rates of Forward Rates :\n");

	

	for(i=1;i<=n;i++)

	{

		BP[i]=((FRBP[i]-BP[0])/BP[0])*(12/m[i])*100;

		AP[i]=((FRAP[i]-AP[0])/AP[0])*(12/m[i])*100;

	}

	

		printf("\nMaturity \t Bid Price\t Ask Price\n");



	for(i=0;i<=n;i++)

	{

		printf(" %d\t\t %f\t%f\n",m[i],BP[i],AP[i]);	

		

 	}	

getch();

}





	
