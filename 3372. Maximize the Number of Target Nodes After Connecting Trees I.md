# 📍Description ➡:-
<!-- Describe your first thoughts on how to solve this problem. -->
There exist two undirected trees with n and m nodes, with distinct labels in ranges [0, n - 1] and [0, m - 1], respectively.

You are given two 2D integer arrays edges1 and edges2 of lengths n - 1 and m - 1, respectively, where edges1[i] = [ai, bi] indicates that there is an edge between nodes ai and bi in the first tree and edges2[i] = [ui, vi] indicates that there is an edge between nodes ui and vi in the second tree. You are also given an integer k.

Node u is target to node v if the number of edges on the path from u to v is less than or equal to k. Note that a node is always target to itself.

Return an array of n integers answer, where answer[i] is the maximum possible number of nodes target to node i of the first tree if you have to connect one node from the first tree to another node in the second tree.

Note that queries are independent from each other. That is, for every query you will remove the added edge before proceeding to the next query.


# 📝Code ⬇:-


# Java
```java []

class Solution {
    public void bfs(ArrayList<ArrayList<Integer>> tree,int node,int[] arr,int k){
        int res=0;
        Queue<Integer> q=new LinkedList<>();
        HashSet<Integer> visited=new HashSet<>();
        q.add(node);
        int count=0;
        while(!q.isEmpty() && count<=k){
            int size=q.size();
            for(int i=0;i<size;i++){
            int temp=q.poll();
            visited.add(temp);
            for(int x:tree.get(temp)){
                if(!visited.contains(x)){
                    q.offer(x);
                }
            }
            }
            count++;
        }
        arr[node]=visited.size();
    }
    
    public int[] maxTargetNodes(int[][] edges1, int[][] edges2, int k) {
        int n=edges1.length+1;
        int m=edges2.length+1;

        ArrayList<ArrayList<Integer>> tree1=new ArrayList<>();
        ArrayList<ArrayList<Integer>> tree2=new ArrayList<>();

        for(int i=0;i<n;i++)tree1.add(new ArrayList<>());
        for(int i=0;i<m;i++)tree2.add(new ArrayList<>());

        for(int[] e:edges1){
            tree1.get(e[0]).add(e[1]);
            tree1.get(e[1]).add(e[0]);
        }

        for(int[] e:edges2){
            tree2.get(e[0]).add(e[1]);
            tree2.get(e[1]).add(e[0]);
        }

        int[] tar1=new int[n];
        int[] tar2=new int[m];

        for(int i=0;i<m;i++){
            bfs(tree2,i,tar2,k-1);
        }
        
        int max=0;
        for(int i:tar2){
            max=Math.max(i,max);
        }

        for(int i=0;i<n;i++){
            bfs(tree1,i,tar1,k);
        }
        
        for(int i=0;i<n;i++){
            tar1[i]+=max;
       }
        
        return tar1;
    }
}

```

# C++
``` cpp []
class Solution {
public:
    vector<vector<int>> buildList(const vector<vector<int>>& edges) {
        vector<vector<int>> adj(edges.size() + 1);
        for (auto &e : edges) {
            adj[e[0]].push_back(e[1]);
            adj[e[1]].push_back(e[0]);
        }
        return adj;
    }
    
    int dfs(const vector<vector<int>>& adj, int u, int p, int k) {
        if (k < 0) return 0;
        int cnt = 1;
        for (int v : adj[u])
            if (v != p) cnt += dfs(adj, v, u, k-1);
        return cnt;
    }
    
    vector<int> maxTargetNodes(vector<vector<int>>& edges1, vector<vector<int>>& edges2, int k) {
        auto adj1 = buildList(edges1), adj2 = buildList(edges2);
        int n = adj1.size(), m = adj2.size(), maxiB = 0;
        vector<int> res(n);

        for (int i = 0; i < m; i++) maxiB = max(maxiB, dfs(adj2, i, -1, k - 1));
        for (int i = 0; i < n; i++) res[i] = dfs(adj1, i, -1, k) + maxiB;
        return res;
    }
};
```

# Python
``` python []
class Solution(object):
    def buildList(self, edges):
        n = len(edges) + 1
        adj = [[] for _ in range(n)]
        for u, v in edges:
            adj[u].append(v)
            adj[v].append(u)
        return adj

    def dfs(self, adj, u, p, k):
        if k < 0:
            return 0
        cnt = 1
        for v in adj[u]:
            if v != p:
                cnt += self.dfs(adj, v, u, k - 1)
        return cnt

    def maxTargetNodes(self, edges1, edges2, k):
        adj1 = self.buildList(edges1)
        adj2 = self.buildList(edges2)
        maxiB = 0
        for i in range(len(adj2)):
            maxiB = max(maxiB, self.dfs(adj2, i, -1, k - 1))
        res = []
        for i in range(len(adj1)):
            res.append(self.dfs(adj1, i, -1, k) + maxiB)
        return res     
```

---

>    **Coded** By $$Panjiyar EDITION 🖋  $$

               
