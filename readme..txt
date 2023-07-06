My Sudoku solver uses a depth first search with constraint satisfaction inspired by the 8 Queens algorithm.

The first decisions I made were the data structures to represent the Sudoku board. The final values being a numpy array,
for my possible values for each cell I used a 2D numpy array of lists. That way, each cell can be accesses by indexing the row and column 
and would store a list of possible values. I chose that over a dictionary that would use a tuple as a key
because I could use inbuilt numpy array function that would make my algorithm faster. The advantage of a dictionary was to reduce look-up
time but every time I access possible values they are for a specific and known coordinate, I never iterate through the possible values of a 
board so I stuck to a 2D numpy array of lists.

Since the Sudokus would have one or no solutions, I decided on a backtracking algorithm in a depth first search. That would reduce the 
branching factor and make the algorithm faster. The first solution found in the tree would be enough.

I used 3 heuristics to optimise the search time.
1) Minimum remaining value:
Choose the cell which has the least possible values. This leads to the smallest branching factor so less time spent exploring the child node.

2) Best degree:
If two cells have the same number of possible values to set, we use a degree heuristic to evaluate which position affects the most 
unassigned cells, that position would then be assigned first.

3) Least constraining value:
Assign a value to a cell which constraints the least number of other cells. This increases the chance of finding the correct solution as
we are trying the value that is closest to the state being solved.

In order to improve the execution time especially for the hard sudokus, I could implement multi-threading, to execute in parallel
some functions. Any more heuristics could not improve the solving time.

