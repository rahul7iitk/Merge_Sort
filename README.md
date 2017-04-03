# Merge_Sort
#include <stdio.h>
#include <stdlib.h>

void sort(int*,int,int);
void merge(int*,int,int,int);

int main(void) {
	
	int n;
	
	scanf("%d",&n);
	
	int* arr=(int*)malloc(n*sizeof(int));
	
	for(int i=0;i<n;i++)
	scanf("%d",&arr[i]);
	
	sort(arr,0,n-1);
	
	for(int i=0;i<n;i++)
	printf("%d ",arr[i]);
	
	return 0;
	
}

void sort(int* arr,int start,int end)
{
    if(start==end)
    return;
    
    int middle=(start+end)/2;
    
    sort(arr,start,middle);
    sort(arr,middle+1,end);
    
    merge(arr,start,middle,end);
    
}

void merge(int* arr,int start,int middle,int end)
{
    int n=end-start+1;
    
    int temparr[n];
    
    int i=start,j=middle+1,k=0;
    
    
    
    while(k<n)
    {
        if(i<=middle&&j<=end)
        {
         if(arr[i]<=arr[j])
         {temparr[k]=arr[i];
         i++;
         }
         
         else
         {temparr[k]=arr[j];
         j++;
         }
        k++;
        }
        else if(i>middle)
        {
            temparr[k]=arr[j];
            j++;
            k++;
        }
        else
        {
            temparr[k]=arr[i];
            i++;
            k++;
        }
    }
    
   k=0;
   
    for(int r=start;r<=end;r++,k++)
    arr[r]=temparr[k];
    
}
    




















