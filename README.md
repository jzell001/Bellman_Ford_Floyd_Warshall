<h1>
Algorithms: Bellman-Ford / Floyd-Warshall
</h1>


------------------------------------------<br />
Description <br />
------------------------------------------<br />
This project conducts analysis on finding the shortest weighted paths in a 
graph by comparing repeated use of the Bellman-Ford algorithm versus the 
Floyd-Warshall algorithm.

We will be using both of the algorithms to compare the run-times of each 
algorithm. In addition, they are both dynamic programming algorithms.

------------------------------------------<br />
Introduction: <br />
------------------------------------------<br />

- What is the problem that we are solving?
  
  The problem we are trying to solve is determining the shortest path, as 
  defined as the total weight between two vertices, for all vertices in a 
  graph.

- What methods are we going to use to solve the problem?

  The methods we are going to use to solve the problem are running 
  Bellman-Ford's algorithm using each vertex as the starting point 
  (i.e., if |V| is the number of vertices, then we will run Bellman-Ford's 
  algorithm |V| times) and then running Floyd-Warshall's algorithm, which 
  calculates all the shortest paths simultaneously.
  
- Why are these good methods to use?

  Although neither of these algorithms can be utilized if there is a negative 
  weight cycle in the graph, they are both good methods to use as they can both 
  be used if there are negative weight edges involved.

------------------------------------------<br />
Bellman-Ford: <br />
------------------------------------------<br />

- What is the Bellman-Ford algorithm?

  The Bellman-Ford algorithm computes the shortest path, as defined by the 
  total sum of the weights between the vertices, from a single source vertex 
  to all other vertices in the directed weighted graph.

- Why are we using it?

  The Bellman-Ford algorithm is being used because it is a dynamic programming 
  algorithm that can be utilized on graphs that have negative weight edges, and 
  because it can be adapted to find the shortest weighted path among all 
  vertices in the graph.
  
- How can we adapt it to work for all-pairs as opposed to single pair?

  The Bellman-Ford algorithm can be adapted to work for all-pairs simply by 
  looping through each vertex as the source vertex and then computing 
  Bellman-Ford on each source vertex in the for loop.
  
- What is the run-time of the algorithm before and after the adaptation?

  The original run-time of the Bellman-Ford algorithm before the adaptation 
  was O(|V| |E|) where |V| is the number of vertices and |E| is the number of 
  edges. After adapting the algorithm to calculate the shortest path among all 
  vertices, the run-time becomes O(|V|^2 |E|) as it is run |V| times with each 
  costing O(|V| |E|)
time.

------------------------------------------<br />
Floyd-Warshall: <br />
------------------------------------------<br />

- What is the Floyd-Warshall algorithm?

  The Floyd-Warshall algorithm computes the shortest path, as defined by the 
  total sum of the weights between the vertices, for all pairs of vertices in 
  the directed weighted graph.
  
- Why are we using it?

  The Floyd-Warshall algorithm is being used because it is a dynamic 
  programming algorithm that can be utilized on graphs that have negative 
  weight edges, and because it is able to find the shortest weighted path 
  among all vertices in the graph at once.
  
- How is it better than the Bellman-Ford algorithm?

  The Floyd-Warshall algorithm is better than the Bellman-Ford algorithm 
  because it is able to calculate the shortest path between all pairs of 
  vertices in the graph at once, without having to be adapted to do so. In 
  addition, is better than the Bellman-Ford because it has a faster 
  run-time, as will be described in more detail during the "Results" section 
  below.
  
- What is the run-time of the algorithm?

  The run-time of the Floyd-Warshall algorithm is O(|V|^3) since it involves 
  three nested for-loops, each having a run-time of O(|V|).

------------------------------------------<br />
Command Line Arguments <br />
------------------------------------------<br />

Example:  python bellman_ford.py -b input1.txt

-b | -f | -both <br />
  (required) Specifies the type of algorithm to be run (Bellman-Ford, 
  Floyd-Warshall, or both)

    -b - Bellman-Ford algorithm 
    -f - Floyd-Warshall algorithm 
    -both - both the Bellman-Ford and Floyd-Warshall algorithms
    
input1.txt | input2.txt <br />
  (required) Specifies the input file of the data that the algorithms will be
  run on
  
    input1.txt - data file with 4 vertices and 5 edges
    input2.txt - data file with 10 vertices and 18 edges
    
------------------------------------------<br />
Design Decisions & Issues <br />
------------------------------------------<br />

Output: <br />
  For each .txt file that is passed in as an argument, for a given algorithm,
  The output contains a list of tuples with each pair of vertices as the
  first element of the tuple and the summation of the weights along the
  shortest path for those two vertices as the second element of the tuple, 
  along with the runtime for the algorithm. For the Bellman-Ford algorithm, 
  it also output whether or not there was a negative cycle within the graph. 
  When both algorithms are called, it outputs both of the above information 
  for each algorithm. 
                
  Note: it should be noted that when the files were inputted into the program,
        all the data was still in string format. Thus it had to be converted to
        float format. Then, prior to outputting the information to a file, the
        values had to be converted back into a string format.
                
Run Time: <br />
  Calculating the runtime of each algorithm was accomplished importing the 
  'time' and utilizing it's 'time.clock()' method which obtains the current 
  time. This can then be used to subtract an earlier time to determine how 
  much time has passed.
  
  Example:  before an algorithm is called, a time was stored as
  
                  start_time=time.clock()
            
  then after the algorithm was run, the runtime was calculated by
            
                  runtime=time.clock()-start_time
  
  
      
