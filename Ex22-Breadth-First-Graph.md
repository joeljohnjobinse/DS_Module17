# Ex22 Breadth First Graph
## DATE: 15/04/2025
## AIM:
To write a printQueue C function of the given graph that is to be traversed in the breadth first manner.

![image](https://github.com/user-attachments/assets/f483f48c-6af0-4027-a993-01c108a50933)


## Algorithm
1. Create an adjacency list or matrix to represent the graph.
2. Use a queue to keep track of the next vertex to visit.
3. Maintain a visited array to avoid revisiting nodes.
4. Enqueue the starting node and mark it as visited.
5. While the queue is not empty:
   a. Dequeue a vertex and print it.
   b. Enqueue all adjacent unvisited vertices and mark them as visited.

## Program:
```
/*
Program to traverse graph using BFS
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

int adj[MAX][MAX];
int visited[MAX];
int queue[MAX];
int front = 0, rear = 0;
int vertices;

void enqueue(int vertex) {
    queue[rear++] = vertex;
}

int dequeue() {
    return queue[front++];
}

int isQueueEmpty() {
    return front == rear;
}

void BFS(int start) {
    enqueue(start);
    visited[start] = 1;

    printf("BFS traversal: ");

    while (!isQueueEmpty()) {
        int current = dequeue();
        printf("%d ", current);

        for (int i = 0; i < vertices; i++) {
            if (adj[current][i] == 1 && !visited[i]) {
                enqueue(i);
                visited[i] = 1;
            }
        }
    }

    printf("\n");
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
        // For undirected graph also add: adj[v][u] = 1;
    }

    int start;
    printf("Enter the starting vertex for BFS: ");
    scanf("%d", &start);

    BFS(start);

    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/585b0f38-e564-4efc-b254-2540be22c9d2)


## Result:
Thus, the code for the printQueue function of the following graph that is to be traversed in the breadth first manner is implemented successfully.
