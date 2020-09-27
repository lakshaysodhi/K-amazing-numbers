# K-amazing-numbers
#include <bits/stdc++.h>
using namespace std;
#define ll long long


int main()
{

    int t;
    cin>>t;
    while(t--){

        int n;
        cin>>n;
        vector<int> A(n);
        vector<vector<int> > index(n+1);

        for(int i=0;i<n;i++){
            cin>>A[i];
            index[A[i]].push_back(i+1);
        }
        unordered_map<int,int> length;
        for(int i=0;i<=n;i++){
            if(index[i].size()>0){
                    length[i]=index[i][0]-0;
                    if(index[i].size()>1){
                for(int j=1;j<index[i].size();j++){
                    if(length[i]<index[i][j]-index[i][j-1]){
                        length[i]=index[i][j]-index[i][j-1];
                    }
                }
                    }
                if(length[i]<n-index[i][index[i].size()-1]+1){
                    length[i]=n-index[i][index[i].size()-1]+1;
                }

            }
        }
        vector<int> K(n+1);
        for(auto it=length.begin();it!=length.end();it++){
            if(K[it->second]==0){
                K[it->second]=it->first;
            }else{
                if(K[it->second]>it->first)
                    K[it->second]=it->first;
            }
        }
        int x=0;
        for(int i=1;i<n+1;i++){
            if(K[i]==0 && x==0) cout<<-1<<" ";
            else {
                    if(x==0){
                        cout<<K[i]<<" ";
                        x=K[i];
                    }else if(K[i]!=0){
                        if(x<K[i]) cout<<x<<" ";
                        else {
                            cout<<K[i]<<" ";
                            x=K[i];
                        }
                    }
                    else cout<<x<<" ";
        }
        }
        cout<<endl;
    }
    return 0;

}



