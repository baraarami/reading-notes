
 # Graphs
# ![](http://www.mathcs.emory.edu/~cheung/Courses/171/Syllabus/11-Graph/FIGS/Graphs/graph12c.gif)
## What is Graphs ?
- A graph is a non-linear data structure
- can be looked at as a collection of vertices
- connected by line segments named edges.
## Terminology
- `Vertex`: also called a “node”, is a data object that can have zero or more adjacent vertices.
- `Edge`: is a connection between two nodes.
- `Neighbor`: The neighbors of a node are its adjacent nodes
- `Degree`: The degree of a vertex is the number of edges connected to that vertex.
### Undirected Graphs
- graph where each edge is undirected or bi-directional

### Directed Graphs (Digraph)
- graph where every edge is directed.

### Complete Graphs
- A complete graph is when all nodes are connected to all other nodes.

### Connected
- graph that has all of vertices/nodes have at least one edge.

### Disconnected
- graph where some vertices may not have edges.

### Acyclic Graph
- An acyclic graph is a directed graph without cycles.

### Cyclic Graphs
- A Cyclic graph is a graph that has cycles.



#### Complete Graphs:
A Complete graph is a simple undirected graph in which every pair of distinct vertices is connected by a unique edge. 

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/CompleteGraph.PNG)


#### Connected Graphs:
It is a graph in which each node has at least one edge.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/ConnectedGraph.PNG)


#### Disconnected  Graphs:
It is a graph in which some node may not have edges.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/DisconnectedGraph.PNG)


### Acyclic vs Cyclic

#### Acyclic Graph:
An acyclic graph is a directed graph without cycles.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/threeAcyclic.png)


#### Cyclic Graph:
A Cyclic graph is a graph that has cycles.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/cyclic.PNG)

#### What is Weighted Graph?
It is a graph with graph numbers assigned to its edges.

![](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-35/resources/assets/weightGraph.PNG)

By using a weight you can make calculation to find the better path, by calculation the total sum of the eges in each path.


### Traversals:
We can use either use `Breadth First` or `Depth First` in travelling in the gragh.

##### Depth First:
![](https://i.stack.imgur.com/QnStc.png)

##### Breadth First:
![](https://i.ytimg.com/vi/QRq6p9s8NVg/maxresdefault.jpg)

## Graph Representation
- graphs representation:

  - Adjacency Matrix:
    -  is represented through a 2-dimensional array.
  - Adjacency List:
    - the most common way to represent graphs.
    - An adjacency list is a collection of linked lists or array that lists all of the other vertices that are connected.
### Weighted Graphs
- A weighted graph is a graph with numbers assigned to its edges.

### Traversals
- Breadth First
- Depth First
### Real World Uses of Graphs
- GPS and Mapping
- Driving Directions
- Social Networks
- Airline Traffic
- Netflix uses graphs for suggestions of products

















