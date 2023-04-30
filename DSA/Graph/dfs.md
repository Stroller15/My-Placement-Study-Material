`DFS Related Questions and Pattern`

`DFS`

```class Solution {
  public:
    // Function to return a list containing the DFS traversal of the graph
    
    void dfs(vector<int> &ans , vector<int> &visited , vector<int> adj[] , int i) {
        
        if(!visited[i]) {
          ans.push_back(i);
            visited[i] = true;
            for(auto x : adj[i])
               dfs(ans , visited , adj , x);
        }
    }
 
    vector<int> dfsOfGraph(int V, vector<int> adj[]) {
        vector<int> ans;
        vector<int> visited(V+1 , false);
        
            dfs(ans , visited , adj , 0);
        
        return ans;
    }
};
<!-- TC - (V+E)      SC- (V)  -->
