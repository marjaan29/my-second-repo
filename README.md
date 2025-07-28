#include<bits/stdc++.h>
using namespace std;

int main() {
    int nodes, edges, start;


    cout << "Enter number of nodes: ";
    cin >> nodes;
    cout << "Enter number of edges: ";
    cin >> edges;

    
    vector<int> adj[nodes+1];

 
    cout << "Enter edges (node1 node2):" << endl;
    for(int i = 0; i < edges; i++) {
        int a, b;
        cin >> a >> b;
        adj[a].push_back(b);
        adj[b].push_back(a);  
    }

  
    cout << "Enter starting node: ";
    cin >> start;


    int visited[nodes+1] = {0};  
    queue<int> q;
    vector<int> bfs_result;


    visited[start] = 1;
    q.push(start);

    while(!q.empty()) {
        int current = q.front();
        q.pop();
        bfs_result.push_back(current);


        for(int neighbor : adj[current]) {
            if(visited[neighbor] == 0) {  
                visited[neighbor] = 1;   
                q.push(neighbor);         
            }
        }
    }

   
    cout << "BFS Traversal: ";
    for(int node : bfs_result) {
        cout << node << " ";
    }
    cout << endl;

    return 0;
}
