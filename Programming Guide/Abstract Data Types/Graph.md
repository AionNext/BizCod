# Graph Abstract Data Type

A graph data structure consists of a finite (and possibly mutable) set of vertices (also called nodes or points), together with a set of unordered pairs of these vertices for an undirected graph or a set of ordered pairs for a directed graph. These pairs are known as edges (also called links or lines), and for a directed graph are also known as edges but also sometimes arrows or arcs. The vertices may be part of the graph structure, or may be external entities represented by integer indices or references.

Here is a formal definition of Graph Data Type 

```js
    define model <graph-name> 
        vertices (Vertex)*
        edges (Edge)*
```

A graph data structure may also associate to each edge some edge value, such as a symbolic label or a numeric attribute (cost, capacity, length, etc.).
The graph abstract data type (ADT) is defined as follows:

- **Graph()** creates a new, empty graph.
- **addVertex(vert)** adds an instance of Vertex to the graph.
- **addEdge(fromVert, toVert)** Adds a new, directed edge to the graph that connects two vertices.
- **addEdge(fromVert, toVert, weight)** Adds a new, weighted, directed edge to the graph that connects two vertices.
- **getVertex(vertKey)** finds the vertex in the graph named vertKey.
- **getVertices()** returns the list of all vertices in the graph.
- **in** returns True for a statement of the form vertex in graph, if the given vertex is in the graph, False otherwise.

