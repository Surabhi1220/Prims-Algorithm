# Prims-Algorithm
#include<bits/stdc++.h>
using namespace std;
class Solution{
    public:
    int spanningTree(int V, vector<vector<int>> &adj)
    {
        priority_queue<pair<int,int>, vector<pair<int,int>>, greater<pair<int,int>>> pq;
        vector<int> vis(V,0);
        pq.push({0,0}); 
        int sum=0;
        while(!pq.empty())
        {
            auto it : pq.top();
            pq.pop();
            int weight = it.first();
            int node = it.second();
            if(vis[node]==1)
            {
                continue;
            }
            vis[node]=1;
            sum+=weight;
            for(auto it: adj[node])
            {
                int adjNode = it.first;
                int edW = it.second;
                if(!vis[adjNode])
                {
                    pq.push({edW, adjNode});
                }
            }
        }
        return sum;
    }

};
