# Sistem-Operaso-FcFs.Code
#include<iostream>
using namespace std;

void  fwait(int proc[],int n,int btime[],int wtime[]){
 wtime[0]=0;

 for(int i=1;i<n;i++)
  wtime[i]=btime[i-1]+wtime[i-1];
}
void fturna(int proc[],int n,int btime[],int wtime[],int tt[]){
 for(int i=1;i<0;i++)
  tt[i]=btime[i]+wtime[i];
}
void favg( int proc[],int n,int btime[]) { 
    int wtime[n],tt[n],total_wt=0,total_tt = 0; 

    fwait(proc,n,btime,wtime); 

    fturna(proc,n,btime,wtime,tt); 
  
    cout << "proc  "<< " Burst time  "
         << " Waiting time  " << " Turn around time\n"; 

    for (int  i=0; i<n; i++) { 
        total_wt=total_wt+wtime[i]; 
        total_tt=total_tt+tt[i]; 
        cout << "   " << i+1 << "\t\t" << btime[i] <<"\t    "
            << wtime[i] <<"\t\t  " << tt[i] <<endl; 
    } 
    cout << "Average waiting time = " 
         << (float)total_wt / (float)n; 
    cout << "\nAverage turn around time = " 
         << (float)total_tt / (float)n; 
} 
int main() 
{ 
    int proc[] = { 1, 2, 3}; 
    int n = sizeof proc / sizeof proc[0]; 
  
    int  b_time[] = {10, 5, 8}; 
  
    favg(proc, n,  b_time); 
    return 0; 
}
