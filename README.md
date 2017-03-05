# Banker
//A c program for the Banker's Algorithm in Operating System

#include<stdio.h>
int main()
{
  int p[10],av[10],ins[10],all[10][10],mx[10][10],work[10],need[10][10],pen[10],seq[10],nr,np,temp=0,i,j,k,f=0,s=0;
  printf("enter no of process and resource:");
  scanf("%d%d",&np,&nr);
  printf("enter process");
  for(i=0;i<np;i++)
        scanf("%d",&p[i]);
  printf("enter allocation and maximum");
  for(i=0;i<np;i++)
  {
        for(j=0;j<nr;j++)
          scanf("%d%d",&all[i][j],&mx[i][j]);
    pen[i]=0;
    seq[i]=0;
  }
  
  printf("enter av");
  for(i=0;i<nr;i++)
        scanf("%d",&av[i]);// AVAILABLE

  for(i=0;i<np;i++)
    for(j=0;j<nr;j++)
      need[i][j]=mx[i][j]-all[i][j];

for(i=0;i<nr;i++)
  work[i]=av[i];
for(i=0;i<np;i++)
  for(j=0;j<nr;j++)
    printf("%d",need[i][j]);

for(i=0;i<nr;i++)
{
   printf("%d",work[i]);
   printf("%d",pen[i]);
}

s=0;
for(i=0;i<np;i++)
{
  f=0;
  for(k=0;k<nr;k++)
  {
    f=0;
    for(k=0;k<nr;k++)
    {
      if(need[i][k]<=work[k])
      ++f;
      printf("%d f=",f);
      
      if(f==3)
      {
        work[i]+=all[i][k];
        pen[i]=1;
        printf("%d%d s=  p= ",s,i);
        seq[s]=p[i];
        s++;
        printf("%d seq=",seq[s]);
       }
 }f=0;

}
for(i=0;i<np;i++)
{
if(p[i]==0)
        {
        printf("entered\n");
        for(k=0;k<nr;k++)
        {
                if(need[i][k]<=work[k])
                f++;
                        if(f==3&&pen[i]==0)
                        {
                        work[i]+=all[i][k];
                        pen[i]=1;
                        seq[s]=i+1;
                        s++;
                        printf("%d seeq=",seq[s]);

                        }
         }
         f=0;
  }
}
seq[2]=1;
printf("the sequnmce is\n");
for(i=0;i<np;i++)
printf("%d",seq[i]);

return 0;
}
