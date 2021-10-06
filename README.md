# Merge-Sort-in-C

#include<stdio.h>

void printarray(int *A , int n){
    int i;
    for(i=0;i<n;i++){
        printf("%d",A[i]);
        
    }
    printf("\n");
    
}

void merge(int A[] ,  int mid ,int low,  int high ){
    int i=low;
    int j=mid+1;
    int k=low;
    int B[100];
    while(i<=mid && j<=high){
        if(A[i]<A[j]){
            B[k]=A[i];
            i++;
            k++;
            
            
        }
        else{
            B[k]=A[j];
            j++;
            k++;
        }
        
    }
       //loop is use for copy rest of the elements 
        while(i<=mid){
            B[k]=A[i];
            k++;
            i++;
            
        }
       //loop is use for copy rest of the elements 
        while(j<=high){
            B[k]=A[j];
            k++;
            j++;
            
        }
        
        //we have to store the result of subarray to the orignal array 
        for(i=low;i<=high;i++){
            A[i]=B[i];
            
        }
        
    
}


void mergesort(int A[] , int low , int high){
    int mid;
    if(low<high){
            mid=(low+high)/2;
            mergesort(A,low,mid);
            mergesort(A,mid+1,high);
            merge(A,mid,low,high);
    
        
    }

}


int main(){
    int A[]={44,77,77,44,8,9,11};
    int n=7;
    printarray(A,n);
    mergesort(A,0,6);
    printarray(A,n);
    
    
    return 0;
}
