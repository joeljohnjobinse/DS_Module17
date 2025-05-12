# Ex24 Topological Sort
## DATE: 16/04/2025
## AIM:
To compose the code to determine whether the topological ordering for the following graph is possible or not.

![image](https://github.com/user-attachments/assets/c74a7111-9b59-475c-aad4-9baf23d50ec0)


## Algorithm
1. Initialize the graph using adjacency list and in-degree array.
2. Add edges and compute in-degrees of each vertex.
3. Enqueue all vertices with in-degree 0.
4. Apply Kahn’s Algorithm:
   a. Dequeue vertex from the queue.
   b. For all its adjacent vertices, reduce in-degree by 1.
   c. If in-degree of adjacent vertex becomes 0, enqueue it.
5. If all vertices are processed, topological sort is possible.
6. Otherwise, a cycle exists and topological sort is not possible.

## Program:
```
/*
Program to determine whether the topological ordering for the following graph is possible or not
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <stdlib.h>

#define MAX 100

int adj[MAX][MAX];
int indegree[MAX];
int n = 5; // Number of vertices: 0,1,2,3,4

void addEdge(int u, int v) {
    adj[u][v] = 1;
    indegree[v]++;
}

int main() {
    int i, j, count = 0;
    int queue[MAX], front = 0, rear = -1;

    // Initialize adjacency matrix and indegree
    for (i = 0; i < n; i++) {
        indegree[i] = 0;
        for (j = 0; j < n; j++) {
            adj[i][j] = 0;
        }
    }

    // Graph edges: 0→1, 0→2, 2→3, 3→1, 1→2, 2→4
    addEdge(0, 1);
    addEdge(0, 2);
    addEdge(2, 3);
    addEdge(3, 1);
    addEdge(1, 2);
    addEdge(2, 4);

    // Enqueue vertices with in-degree 0
    for (i = 0; i < n; i++) {
        if (indegree[i] == 0)
            queue[++rear] = i;
    }

    printf("Topological Sort (if possible): ");
    while (front <= rear) {
        int u = queue[front++];
        printf("%d ", u);
        count++;

        for (j = 0; j < n; j++) {
            if (adj[u][j] == 1) {
                indegree[j]--;
                if (indegree[j] == 0)
                    queue[++rear] = j;
            }
        }
    }

    printf("\n");

    if (count != n)
        printf("Result: Topological ordering NOT possible (cycle detected).\n");
    else
        printf("Result: Topological ordering IS possible.\n");

    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/ca43a277-1585-4599-b905-46f57b4543c4)


## Result:
Thus, the C program for determining whether the topological ordering for the following graph is possible or not, is implemented successfully.
