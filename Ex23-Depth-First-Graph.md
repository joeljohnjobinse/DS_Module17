# Ex23 Depth First Graph
## DATE: 15/04/2025
## AIM:
To compose the code for the function createNode to traverse the graph below in the depth first fashion.

![image](https://github.com/user-attachments/assets/63552824-d0a3-49c6-a473-6db27d1f03e4)

## Algorithm
1. Initialize an adjacency matrix to represent the graph.
2. Create a visited[] array to track visited nodes.
3. Define a DFS() function that:
   a) Prints the current node.
   b) Marks it as visited.
   c) Recursively visits all adjacent unvisited nodes.
4. Start DFS from the desired source node. 

## Program:
```
/*
Program to traverse the graph below in the depth first fashion
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>

#define MAX 10

int adj[MAX][MAX];
int visited[MAX];
int vertices;

void DFS(int vertex) {
    printf("%d ", vertex);
    visited[vertex] = 1;

    for (int i = 0; i < vertices; i++) {
        if (adj[vertex][i] == 1 && !visited[i]) {
            DFS(i);
        }
    }
}

int main() {
    int edges, u, v;

    printf("Enter number of vertices: ");
    scanf("%d", &vertices);

    printf("Enter number of edges: ");
    scanf("%d", &edges);

    // Initialize adjacency matrix and visited array
    for (int i = 0; i < vertices; i++) {
        visited[i] = 0;
        for (int j = 0; j < vertices; j++) {
            adj[i][j] = 0;
        }
    }

    printf("Enter edges (format: from to):\n");
    for (int i = 0; i < edges; i++) {
        scanf("%d%d", &u, &v);
        adj[u][v] = 1;
        // For undirected graph, also do: adj[v][u] = 1;
    }

    int start;
    printf("Enter the starting vertex for DFS: ");
    scanf("%d", &start);

    printf("DFS traversal: ");
    DFS(start);
    printf("\n");

    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/38f3c595-8171-4088-862e-b9802168de9b)


## Result:
Thus, the C code for the function createNode to traverse the graph below in the depth first fashion is implemented successfully
