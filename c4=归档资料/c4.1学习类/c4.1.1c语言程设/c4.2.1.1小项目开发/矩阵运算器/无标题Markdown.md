//2021/1/7
//矩阵计算器 



#include<stdio.h> 
#include<windows.h>
#define N 50 
//矩阵含有的信息：行数，列数，计划用结构体实现
typedef struct 
{
	float mat[N][N];
	int row;
	int clo;
	
} matrix;

//全局定义输入输出矩阵 

matrix ma,mb,mc;

//矩阵输入
 void input()
 {  int ch,i,j;
 	printf("请选择输入一个（1）或两个矩阵（2）:");
	repeat:scanf("%d",&ch);
			if(ch!=1&&ch!=2)
			{
				printf("无效输入!请重新选择:");
				fflush(stdin);
				goto repeat;
				
		     }
 	if(ch==1)
 	{
 		printf("请输入矩阵的行数和列数，中间以空格隔开\n");
 		scanf("%d %d",&ma.row,&ma.clo);
 		printf("请按行顺序输入矩阵的每个数值，值间以空格隔开，各行间以回车隔开:\n");
 		for(i=1;i<=ma.row;i++)
 		{
 			for(j=1;j<=ma.clo;j++)
 			{
 				scanf("%f",&ma.mat[i][j]);
 				
			 }
 			
 			
		 }
	 }
 	else 
 	{
 	  	printf("请输入两个矩阵的行数和列数，值间以空格隔开，各行间以回车隔开:\n"
		       "示例：矩阵1:3 5 矩阵2：5 7\n");
 		printf("矩阵1:"); 
		scanf("%d%d",&ma.row,&ma.clo);
		printf("矩阵2:");
		scanf("%d%d",&mb.row,&mb.clo);
 		printf("请按行顺序输入矩阵1的每个数值，数值间以空格隔开，各行间以回车隔开:\n");
 		for(i=1;i<=ma.row;i++)
 		{
 			for(j=1;j<=ma.clo;j++)
 			{
 				scanf("%f",&ma.mat[i][j]);
 				
			 }
		}
 		printf("请按行顺序输入矩阵2的每个数值，值间以空格隔开，各行间以回车隔开:\n");
 		for(i=1;i<=mb.row;i++)
 		{
 			for(j=1;j<=mb.clo;j++)
 			{
 				scanf("%f",&mb.mat[i][j]);
 				
			 }
 		}
	  printf("\n\t运算完成,结果如下:\n");
	 printf("\t\t");
	 for(i=1;i<=ma.row;i++)
	 {
	 	for(j=1;j<=mb.clo;j++)
	 	{
	 		printf(" %f  ",mc.mat[i][j]);
	 		
		 }
		 printf("\n");	
	 }
     Sleep(10000);
 
 
}
}
//矩阵加减法
void add_minus(char  sign)
{     int i,j;
     system("cls");
	 system("color 4e"); 	
	  printf("\n\n");
	  for(i=0;i<=12;i++)
	  {printf("  \t==");
	  }
     
     if(ma.row!=mb.row||ma.clo!=mb.clo)
     {
     	printf("这两个矩阵不能做加法\n");
     	Sleep(5000);
     	return ;
	 }
	 mc.row=ma.row;
	 mc.clo=ma.clo;
	if(sign=='+')
	{
			for(i=1;i<=ma.row;i++)
 		{
 			for(j=1;j<=ma.clo;j++)
 			{
 				mc.mat[i][j]=ma.mat[i][j]+mb.mat[i][j];
 				
			 }

	}
}
	else 
	{       printf("默认先输入的矩阵减后输入的矩阵\n");
			for(i=1;i<=ma.row;i++)
 		{
 			for(j=1;j<=ma.clo;j++)
 			{
 				mc.mat[i][j]=ma.mat[i][j]-mb.mat[i][j];
 				
			 }
		
		
	}
     
     
     for(i=1;i<=ma.row;i++)
     {
     	for(j=1;j<=ma.clo;j++)
     	{
     		printf(" %f  ",mc.mat[i][j]);
     		
		 }
    
	 }


 } 
  printf("\n\t运算完成,结果如下:\n");
	 for(i=1;i<=mc.row;i++)
	 {
	 	for(j=1;j<=mc.clo;j++)
	 	{
	 		printf(" %f  ",mc.mat[i][j]);
	 		
		 }
		 printf("\n");	
	 }
     Sleep(10000);
}


//矩阵乘法 
void mutiply()
{   int i,j,k;
     system("cls");
	 system("color 4e"); 	
	  printf("\n\n");
	  for(i=0;i<=12;i++)
	  {printf("  \t==");
	  }
	if(ma.clo!=mb.row)
	{printf("两个矩阵不能相乘\n");
	Sleep(5000);
	return ;
	}
	for(i=1;i<=ma.row;i++)
	{
		for(k=1;k<=mb.clo;k++)
		
		{
			float sum=0;
		for(j=1;j<=ma.clo;j++)
		{
			
			sum+=ma.mat[i][j]*mb.mat[j][k];
			
		}
		mc.mat[i][k]=sum;
	  }
		
		
	  }
	 
	 printf("\n\t运算完成,结果如下:\n");
	 for(i=1;i<=ma.row;i++)
	 {
	 	for(j=1;j<=mb.clo;j++)
	 	{
	 		printf(" %f  ",mc.mat[i][j]);
	 		
		 }
		 printf("\n");	
	 }
     Sleep(10000);
}
//进入正题，行列式
void det()
{    int i,j;
	 system("cls");
	 system("color 4e"); 	
	  printf("\n\n");
	  for(i=0;i<=12;i++)
	  {printf("  \t==");
	  }
	  printf("\n");
	if(ma.clo!=ma.row)
	{
		printf("非方阵没有行列式\n");Sleep(5000);
		return ;	
	}

	for(i=1;i<=ma.clo-1;i++)
	{
		//找每列中对角线以下第一个非零元 
		int find=0; 
		for(j=i;j<=ma.row;j++)
		{
			if(ma.mat[j][i]!=0)
			{find=1;
			break;
		}
		 } 
		 //当前列全为零，跳出 
		 if(!find)
		 break;
		 //当前对角线上就是非零元，无需换行 
		 else if(j==i)
		 {
		 	float times;
		 	int k,q;
		 	for(k=i+1;k<=ma.row;k++)
		 	{
		 		times=ma.mat[k][i]/ma.mat[i][i];
				 for(q=i;q<=ma.clo;q++)
				 ma.mat[k][q]-=times*ma.mat[i][q];
		 		
			 }
		 	
		 }
		 //先换行再消元 
		else 
		{
			int k;
			float times,temp;
			for(k=1;k<=ma.clo;k++)
			{
				temp=ma.mat[i][k];
				ma.mat[i][k]=ma.mat[j][k];
				ma.mat[j][k]=temp;
			}
			for(k=i+1;k<=ma.row;k++)
			{
				
				times=ma.mat[k][i]/ma.mat[i][i];
				ma.mat[k][i]-=times*ma.mat[i][i];
			}
			
		}
		
		
		
	}
float mult=1;
		for(i=1;i<=ma.row;i++)
		{
			mult*=ma.mat[i][i];
			
		}
		printf("\n\t\t\t行列式为%f",mult);
		 Sleep(5000);
		
 } 

//矩阵转置
void reverse()
{     int i,j;
      float temp;
	  system("cls");
	  system("color 4e"); 	
	  printf("\n\n");
	  for(i=0;i<=12;i++)
	  {printf("  \t==");
	  }
	
	if(ma.row!=ma.clo)
	{
		printf("非方阵矩阵不能转置\n");
		return ;
		
	}
	else 
	{
		mc.row=ma.row;
		mc.clo=ma.clo;
			for(i=1;i<=mc.row;i++)
		{
			
			
			for(j=1;j<=mc.clo;j++)
			{
				mc.mat[i][j]=ma.mat[i][j];
			}
			
		}
		for(i=1;i<=ma.row-1;i++)
		{
			for(j=i+1;j<=ma.clo;j++)
			{
			   temp=mc.mat[j][i];
			   mc.mat[j][i]=mc.mat[i][j];
			   mc.mat[i][j]=temp;
			}
			
			
		}
	
		 printf("\n\t运算完成,结果如下:\n");
		for(i=1;i<=mc.row;i++)
		{
			
			
			for(j=1;j<=mc.clo;j++)
			{
					printf(" %f  ",mc.mat[i][j]);
			}
			printf("\n");
		}
		Sleep(10000);
	}
	
 } 

/*
//逆矩阵
void inver()
{
	
	
	
	
	
 } 















*/

//主函数，用户输入矩阵行列数 ，输出功能菜单 
int main()
{    int i;
     char sign;
	system("color 4e");
	printf("\n\n");
	for(i=0;i<=12;i++)
	{printf("  \t*");
	}
	printf("\n\n\n\n\t\t\t\t\t");
	char s[22]="欢迎来到哈深矩阵计算器";
	for( i=0;i<=21;i++)
	{
		Sleep(30);
		printf("%c",s[i]);
		
	 } 
	Sleep(500);
	while(1)
	{
	system("cls");
	printf("\n\n");
	for(i=0;i<=12;i++)
	{printf("  \t*");
	}
    printf("\n\n\n");
    printf("      ☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆☆\n");
    printf("      ***********************************************************\n");
    printf("      \t\t\t哈深矩阵计算器\n");
    printf("\n");
    printf("      \t\t1.矩阵输入");
    printf("\t\t2. 矩阵加减法\n");
    printf("      \t\t3. 矩阵乘法");
    printf("\t\t4. 算行列式\n");
    printf("      \t\t5. 伴随矩阵");
    printf("\t\t6.转置矩阵\n");
    printf("      \t\t7.算逆矩阵");
    printf("\t\t8. 返回主菜单\n");
    printf("      ***********************************************************\n");
    printf("      ~~~~~退~~~~~~~~~~出~~~~~~~~~~请~~~~~~~~~~按~~~~~~~~~~9~~~~~\n");
    printf("      -----------------------------------------------------------\n\n");
    printf("请输入你的选择(1~9):");
        loop:scanf("%d",&i);
        if(!(i>=1&&i<=9))
        {   fflush(stdin);
            printf("输入有误,请在1~9中进行选择:");
            goto loop;
        }
	      switch(i)
       {
       	case 1:
       	    input();
       		break;
       		case 2:
       		printf("请选择加法（‘+’）或减法（‘-’）:");
			repeat:scanf(" %c",&sign);
			if(sign!='+'&&sign!='-')
			{
				printf("无效输入!请重新选择:");
				fflush(stdin);
				goto repeat;
				
		     }
		     else add_minus(sign);
       			break;
       			case 3:
       				mutiply();
       				break;
       				case 4:
       				det();
       					break;
       					case 5:
       						//adjoint();
       						break;
       						case 6:
       							reverse();
       							break;
       							case 7:
       								//inver();
       								break;
       								case 8:
       									break;
       									case 9:
       										exit(0); 
       					
       	
	   }
 
   } 
	

}




 