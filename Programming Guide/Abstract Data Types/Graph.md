# Graph Abstract Data Type

A graph data structure consists of a finite (and possibly mutable) set of vertices (also called nodes or points), together with a set of unordered pairs of these vertices for an undirected graph or a set of ordered pairs for a directed graph. These pairs are known as edges (also called links or lines), and for a directed graph are also known as edges but also sometimes arrows or arcs. The vertices may be part of the graph structure, or may be external entities represented by integer indices or references.

Here is a formal definition of Graph Data Type 

```js
    define model <graph-name> 
        vertices (Vertex)*,
        edges (Edge)*,
        type GraphType
```

where a type GraphType is defined 

```js
    define type GraphType = { DIRECTED, UNDIRECTED }
```

**Undirected** graphs have edges that do not have a direction. The edges indicate a two-way relationship, in that each edge can be traversed in both directions. 

**Directed** graphs have edges with direction. The edges indicate a one-way relationship, in that each edge can only be traversed in a single direction.

By default, Graph is undirected.

Here are the definitions for `Vertex` and `Edge` data models:

```js
     define 
           model Vertex 
               id ID,
               name
               
           model Edge
               id Id,
               name,
               source Vertex, 
               target Vertex,
               weight Decimal
               
```


>MEP: So could the vertices be instances of various classes? Would they have to be all the same class or could they be arbitrary?
>
>MEP: I guess if the vertices were an `Interface` class then you could use any class that implements the interface.
>
>MEP: Here's what I'm thinking (not sure if my syntax is correct):

>MS: yes, it is correct. Vertex is an abstract class so any class that inherits from Vertex might be used
```js
    define model Facebook is Graph
        vertices (Person)*
        edges (Friendship)*
        
    define model Person is Vertex        
        
    Mike = Person::create(name='Mike')  
    Mary = Person::create(name='Mary') 
    G = Facebook::create()
    G.addVertex(Mike)
    G.addVertex(Mary)
    G.addEdge(Mike,Mary,10)
    G.addEdge(Mary,Mike,5)
```
A graph data structure may also associate to each edge some edge value, such as a symbolic label or a numeric attribute (cost, capacity, length, etc.).
The graph abstract data type (ADT) is defined as follows:

- **Graph::create()** creates a new, empty instance of graph.
- **addVertex(vert)** adds an instance of Vertex to the graph.
- **addEdge(source, target)** Adds a new, directed edge to the graph that connects two vertices.
- **addEdge(source, target, weight)** Adds a new, weighted, directed edge to the graph that connects two vertices.
- **getVertex(vert)** finds the vertex in the graph by its id or name
- **getEdge(id)** finds the edge in the graph by id.
- **getEdge(source, target)** finds the edge in the graph by source/target pair.
- **getVertices()** returns the list of all vertices in the graph.
- **getEdges()** returns the list of all edges in the graph.
- **in** returns True for a statement of the form vertex in graph, if the given vertex is in the graph, False otherwise.

>MEP: What other functions might we have for doing interesting things with a graph?
>
>MS we will implement basic (typical) functionalities here such as graph traversals, spanning tree, searches and so on. I will provide a full list of basic algorithms implemented for this type
>
>MEP: For example finding a spanning graph, or the shortest path between two vertices
>MEP: Or would we simply leave users to develop their own algorithms for these
>
>MS: if need be, user can add methods (functional expansion) to Graph data type just like any other data type. Refer to Method.md for more information about functional expansion (methods)
>
>MEP: If the `Friendship` edge was defined like this
```js
    define model Friendship is Edge
        dateStarted Date
        dateEnded Date
        duration Number
```

>MEP: Would we be able to do something like this?
>
>MS: yes, this is possible but you would need to find an edge by either its id or source/target pair. Here is a modfied version assuming that there is an edge (Friendship) bertween the vertices Mike and Marek.
>


```js
    G.getEdge(Mike, Marek).dateStarted=currentDate
```

>MEP: There is a type for date. Is there also a type for time?
>
>MS : yes, Date and Time are separate types.
>
>MEP: I suppose we could even define the vertices of a graph to be `graphs` (essentially subgraphs)
>
>MS: yes, in this case the Graph would need to inherit from Vertex
>
>MEP: How would I add an edge that is `not` directed? Would I have to add it twice in each direction?
>
>MS : no, just once. Graph is either directed or undirected.
>
>MEP: When we add a vertex how are we defining/specifying its name?
>
>MS: Vertex has both id and name.

## Graph Algorithms

 **Breadth-first search**
 
 
Traversing or searching is one of the fundamental operations which can be performed on graphs. In breadth-first search (BFS), we start at a particular vertex and explore all of its neighbours at the present depth before moving on to the vertices in the next level.

**Depth-first search**

In depth-first search (DFS) we start from a particular vertex and explore as far as possible along each branch before retracing back (backtracking). In DFS also we have to keep track of the visited vertices. When implementing DFS, we use a stack data structure to support backtracking.

**Topological sorting**


Topological sorting of a graph is a linear ordering of its vertices so that for each directed edge (u, v) in the ordering, vertex u comes before v.

