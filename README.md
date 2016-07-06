# Algorithms Study Guide

O, Θ, and Ω Notation
================================================================================

f(x) = O(g(x)) (big-oh) means that the growth rate of f(x) is asymptotically **less than _or equal to_** to the growth rate of g(x).

f(x) = Ω(g(x)) (big-omega) means that the growth rate of f(x) is asymptotically **greater than _or equal to_** the growth rate of g(x)

f(x) = o(g(x)) (small-oh) means that the growth rate of f(x) is asymptotically **less than** the growth rate of g(x).

f(x) = ω(g(x)) (small-omega) means that the growth rate of f(x) is asymptotically **greater than** the growth rate of g(x)

f(x) = Θ(g(x)) (theta) means that the growth rate of f(x) is asymptotically **equal to** the growth rate of g(x)

[Source](http://stackoverflow.com/a/471206)



Algorithms
================================================================================

Sorting
--------------------------------------------------------------------------------

### Merge Sort

Merge sort uses the divide-and-conquer method on an unsorted array.

**Steps:**

1. Divide the array in half.
2. Recursively divide the resulting arrays in half until they each have one element.
3. Merge the subarrays up into each other until you have a single array.

**Runtime:** Θ(n lg n)

**In place?** No


### Quicksort

**Steps:**

1. Choose a pivot value in the array.
2. Arrange the array elements so that the elements less than the pivot value are placed to its left, and those greater than it are to its right. This is **partitioning**.
   1. Index i starts of pointing to the first element in the array. Index j points to the last.
   2. Move i forward until an element with value greater or equal to the pivot is found.
   3. Move Index j is moved backward, until an element with value lesser or equal to the pivot is found.
   4. If i ≤ j, swap their elements. Then move i forward and j backward one.
   5. When i passes j, the partitioning is complete.
3. Recursively sort the subarrays to the left and right of the pivot by repeating steps 1 and 2. Stop when your subarrays have 1 element.

*Why quicksort over merge sort?* Though merge sort is asymptotically as good or better than quicksort, quicksort has a much smaller constant factor. In practice, quicksort outperforms merge sort.

**Runtime:**

 - Worst-case: O(n<sup>2</sup>)
 - Average-case: O(n lg n)

**In place?** Yes

[Full description and code](http://www.algolist.net/Algorithms/Sorting/Quicksort)



Graphs
--------------------------------------------------------------------------------

### Representations

#### Edge Lists

An edge list is a 2D array where each element contains a source and destination vertex. To add weights, just add a third number to each element.

**Search time:** O(E)

**Space requirement:** Θ(E)


#### Adjacency Matrices

An adjacency matrix is a table where a cell in row i and column j represents an edge (i, j) in the graph. To store weight information, use the weight as the value in the cell and designate a different value like null to denote no edge.

**Search time:** Constant

**Space requirement:** Θ(V<sup>2</sup>)


#### Adjacency Lists

An adjacency list has one array per vertex. Each vertex's array stores the vertices adjacent to it. To store weights, add a second value to each vertex in the lists.

**Search time:** Θ(d) where d is the degree of the vertex you are searching for. d can be between 0 and |V| - 1.

**Space requirement:** 2|E|


### Algorithms

#### Breadth-First Search

BFS stores two values for each vertex in the graph. The first value is the distance of that vertex from the source. The second value is the vertex's predecessor—the vertex that comes before it in the shortest path to the source.

Shortest path algorithm:

1. Start at the source vertex and set its distance to 0.
2. Look at that vertex's neighbors and assign them distances of 1 with predecessors of the source vertex.
3. Look at all neighbors of the vertices with distance 1 _that have not yet been seen_. Assign them a distance of 2 and set their predecessors appropriately.
4. Repeat until all vertices reachable from the source have been seen.

Use a queue to keep track of which vertices have been visited but not yet visited _from_. When you first see a vertex, add it to the queue. To decide which vertex to use next as a "from" vertex, simply dequeue the next vertex. That will be the vertex that has been in the queue the longest.

**Performance:** O(V + E) (each vertex is visited only once, and each edge is visited at most twice, once for each of its connected vertices)



Useful Resources
================================================================================

- [Oregon State University Undergraduate Algorithms Study Guide](https://web.engr.oregonstate.edu/~glencora/wiki/index.php?n=Main.UndergraduateAlgorithmsStudyGuide)
