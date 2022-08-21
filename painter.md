#include<vector>
using namespace std;


bool ispossible(vector<int> &boards,int n,int k, int mid){
    int painters=1;
    int boardsum=0;
    for(int i=0;i<n;i++){
        if(boards[i]+ boardsum<=mid){
            boardsum+=boards[i];
        }
    else {
        painters++;
        if(painters>k||boards[i]>mid){
            return false;
        }
        boardsum=boards[i];
    }
        if(painters>k){
            return false;
        }
    }
    return true;
}

int findLargestMinDistance(vector<int> &boards,int n, int k,int mid)
{
    int s=0;
    int sum=0;
    for(int i=0;i<n;i++){
        sum+=boards[i];
    }
    int e=sum;
    int mid=s+(e-s)/2;
    int ans=-1;
    
    while(s<=e){
        if(ispossible(boards,n,k,mid)){
            ans=mid;
            e=mid-1;     
        }
        else{
            s=mid+1;
        }
        mid=s+(e-s)/2;
    }
    return ans;
}
   
