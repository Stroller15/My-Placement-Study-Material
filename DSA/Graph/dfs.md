`DFS Related Questions and Pattern`

`DFS`

```class Solution {
  private:
    void dfs(vector<int> adj[], vector<int> &ans, vector<int> &vis, int source) {
        // here we check that source node visited or not
        if(!vis[source]) {
            // If not visited then first we will mark as vis
            vis[source] = true;
            
            // we will push that source node as a dfs traversal output
            ans.push_back(source);
            
            for(auto node: adj[source]) {
                
                // we will call dfs from here node that is adjecent of source
                dfs(adj, ans, vis, node);
            }
        }
    }
  public:
    // Function to return a list containing the DFS traversal of the graph.
    vector<int> dfsOfGraph(int V, vector<int> adj[]) {
        // for storing ans of dfs traversal
        vector<int> ans; 
        
        // This is a visited array who insure from looping
        vector<int> vis(V, false);
        
        // here we are calling dfs
            //  we call this dfs call in loop when it will more than one component
        
        dfs(adj, ans, vis, 0);
        
        return ans;
    }
};
<!-- TC - (V+E)      SC- (V)  -->
