# Jump-Search-C-
C++ Jump Search

#include <bits/stdc++.h>
#include <math.h>
using namespace std;

int linearSearch(int *arr,int n, int key,int start){
    for(int i=n-start;i<n;++i){
        if(*(arr+i)==key){
            return i;
        }
    }
    return -1;
}
int jumpSearch(int arr[], int jump, int start, int end,int size, int key){
    if(size>end){
        if(arr[end]==key){
            return end;
        }else if(arr[start]==key){
            return start;
        }
        return jumpSearch(arr, jump, start+jump,end+jump,size,key);
    }
    return linearSearch(arr, size, key, start);
    
}
int main(){
    int size,key,jump;
    cout<<"Enter size of array: ";
    cin>>size;
    
    int arr[size];
    cout<<"Enter elements of array(sorted array): ";
    for(int i=0;i<size;++i){
        cin>>arr[i];
    }
    cout<<"Enter key: ";
    cin>>key;
    jump=sqrt(size);
    cout<<jumpSearch(arr, jump, 0, jump,size, key);
    return 0;
}
