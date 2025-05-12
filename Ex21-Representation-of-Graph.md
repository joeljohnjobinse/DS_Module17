# Ex21 Representation of Graph
## DATE: 15/04/2025
## AIM:
To write a C program to display the adjacency matrix of the given graph by supplying the edges and the number of vertices.

## Algorithm
1. Start by reading the number of vertices v and number of edges e.
2. Initialize a 2D matrix adj[v][v] with all values set to 0.
3. For each edge, read the pair of vertices (src, dest).
4. Set adj[src][dest] = 1 and adj[dest][src] = 1 for an undirected graph (or only one direction for directed).
5. Print the final adjacency matrix.

## Program:
```
/*
Program to display the adjacency matrix of the given graph
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>

int main() {
    int v, e, i, j, u, vertex1, vertex2;
    printf("Enter the number of vertices: ");
    scanf("%d", &v);

    int adj[v][v];

    // Initialize adjacency matrix to 0
    for (i = 0; i < v; i++) {
        for (j = 0; j < v; j++) {
            adj[i][j] = 0;
        }
    }

    printf("Enter the number of edges: ");
    scanf("%d", &e);

    printf("Enter the edges (format: vertex1 vertex2):\n");
    for (i = 0; i < e; i++) {
        scanf("%d%d", &vertex1, &vertex2);
        if (vertex1 >= v || vertex2 >= v || vertex1 < 0 || vertex2 < 0) {
            printf("Invalid edge (%d, %d) - vertex out of bounds.\n", vertex1, vertex2);
            i--; // retry this edge
            continue;
        }
        adj[vertex1][vertex2] = 1;
        adj[vertex2][vertex1] = 1; // Remove this line if the graph is directed
    }

    printf("Adjacency Matrix:\n");
    for (i = 0; i < v; i++) {
        for (j = 0; j < v; j++) {
            printf("%d ", adj[i][j]);
        }
        printf("\n");
    }

    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/e1b362cd-bf1e-4842-8a0f-529bae31e3c3)


## Result:
Thus, the C program to print the adjacency matrix of the given graph is implemented successfully.
