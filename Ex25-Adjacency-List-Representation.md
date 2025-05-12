# Ex25 Adjacency List Representation
## DATE: 16/04/2025
## AIM:
To write a C program to represent the given graph using the adjacency list.

## Algorithm
1. Define a structure for the adjacency list node and the graph.
2. Create a new node for each edge and insert it into the list of the corresponding vertex.
3. Loop through all vertices and print their adjacency lists.
4. This efficiently represents a sparse graph.

## Program:
```
/*
Program to represent the given graph using the adjacency list
Developed by: Joel John Jobinse
RegisterNumber: 212223240062
*/

#include <stdio.h>
#include <stdlib.h>

struct Node {
    int dest;
    struct Node* next;
};

struct Graph {
    int V;
    struct Node** adjList;
};

// Create a new adjacency list node
struct Node* createNode(int dest) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->dest = dest;
    newNode->next = NULL;
    return newNode;
}

// Create a graph with V vertices
struct Graph* createGraph(int V) {
    struct Graph* graph = (struct Graph*)malloc(sizeof(struct Graph));
    graph->V = V;
    graph->adjList = (struct Node**)malloc(V * sizeof(struct Node*));

    for (int i = 0; i < V; i++)
        graph->adjList[i] = NULL;

    return graph;
}

// Add edge to graph (undirected or directed)
void addEdge(struct Graph* graph, int src, int dest) {
    // Add edge src->dest
    struct Node* newNode = createNode(dest);
    newNode->next = graph->adjList[src];
    graph->adjList[src] = newNode;

    // Uncomment for undirected graph:
    /*
    newNode = createNode(src);
    newNode->next = graph->adjList[dest];
    graph->adjList[dest] = newNode;
    */
}

// Print adjacency list
void printGraph(struct Graph* graph) {
    for (int v = 0; v < graph->V; v++) {
        struct Node* temp = graph->adjList[v];
        printf("Adjacency list of vertex %d: ", v);
        while (temp) {
            printf("-> %d ", temp->dest);
            temp = temp->next;
        }
        printf("\n");
    }
}

int main() {
    int V = 5;
    struct Graph* graph = createGraph(V);

    // Example graph: 0->1, 0->4, 1->2, 1->3, 1->4, 2->3, 3->4
    addEdge(graph, 0, 1);
    addEdge(graph, 0, 4);
    addEdge(graph, 1, 2);
    addEdge(graph, 1, 3);
    addEdge(graph, 1, 4);
    addEdge(graph, 2, 3);
    addEdge(graph, 3, 4);

    printGraph(graph);

    return 0;
}

```

## Output:
![image](https://github.com/user-attachments/assets/9c171c1a-2391-46a3-af2c-2f6253e3e19d)


## Result:
Thus, the C program to represent the given graph using the adjacency list is implemented successfully
