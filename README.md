# DSA-Leetcode-problems
DSA concepts and problem solving.
#include<iostream>
#include<queue>
#include<list>

using namespace std;

class Graph{
    int V;
    list<int> * l;

public:
    Graph(int V)
    {
        this->V=V;
        l = new list<int>[V];
    }

    void addEdge(int u,int v)
    {
        l[u].push_back(v);
        l[v].push_back(u);
    }

    void BFS()
    {
        queue<int> Q;
        vector<bool> vis(V,false);
        Q.push(0);
        vis[0]=true;

        while(Q.size()>0)
        {
            int u = Q.front();
            Q.pop();

            cout<<u<<" ";
            for(int v : l[u])
            {
                if(!vis[v])
                {
                    vis[v]=true;
                    Q.push(v);
                }
            }
            
        }
        cout<<endl;

    }

    void DFShelper(int u, vector<bool> &vis)
    {
        cout << u << " ";
        vis[u] = true;
        for (int v : l[u])
        {
            if (!vis[v])
            {
                DFShelper(v, vis);
            }
        }
    }

    void DFS()
    {
        int src = 0;
        vector<bool> vis(V, false);
        DFShelper(src, vis);
        cout << endl;
    }


    void PrintAdjacencyList()
    {
        for(int i=0;i<V;i++)
        {
            cout<<i<<" : ";
            for(int nei: l[i])
            {
                cout<<nei<<" ";
            }
            cout<<endl;
        }
    }
};

int main()
{
    Graph g(5);
    g.addEdge(0,1);
    g.addEdge(1,2);
    g.addEdge(1,3);
    g.addEdge(2,4);
    //g.addEdge(2,4 );

    g.PrintAdjacencyList();   
    cout<<"BFS\n";
    g.BFS();
    cout<<"DFS\n";
    g.DFS();
    
}
