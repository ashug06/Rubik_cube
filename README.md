
# Rubik's Cube Solver Project

# Overview
This project aims to model and simulate a Rubik's Cube using various representations in code. The core functionalities include defining cube operations, representing the cube in different ways, and providing algorithms for solving it.

# Terminology
Cubie: A mini-cube in the Rubik's Cube; can be a Center, Edge, or Corner cubie.
Center Cubie: A cubie with one colored side; 6 total, statically positioned.
Edge Cubie: A cubie with two colored sides; 12 total.
Corner Cubie: A cubie with three colored sides; 8 total.
Face: Each of the six sides of the cube, made up of 9 cubies.

# Operations and Notation
The project utilizes a standard notation system for cube rotations:

Clockwise Moves: F, R, U, B, L, D
Counter-Clockwise Moves: F’, R’, U’, B’, L’, D’
Double Rotations: F2, R2, U2, B2, L2, D2
Planar Representation
A planar representation unfolds the Rubik's Cube into a 2D format, simplifying the visualization of cube states.

# Implementations
Generic Rubik's Cube

An abstract class defines common operations, including:
All 18 rotations
Printing the cube in planar format
Generating a random solvable shuffle
Checking if the cube is solved
3D Array Representation

Utilizes a 3D array (6 x 3 x 3) to store cube colors, allowing for intuitive color manipulation and rotation.
1D Array Representation

Implements a single array of 54 characters to represent the cube. Each position holds the color of a cubie's side, enabling faster operations.
Bitboard Representation

Uses 6 64-bit integers to represent the cube efficiently. Each face is encoded in a way that allows quick rotations using bit manipulation.
Key Concepts
Solvability: Not all permutations of a Rubik's Cube are solvable. The random shuffle function ensures generated states are reachable from a solved state.
Clockwise Indices: The indexing of stickers and faces follows a clockwise pattern, simplifying face rotation operations.
References
Abstract Classes and Virtual Functions: Learn C++
Representing the Rubik's Cube in Different Ways
Overview
To solve the Rubik's Cube using algorithms, we first need to represent its various states.

<u>Key Information:</u>
States: There are approximately 43 quintillion possible configurations of the Rubik’s Cube.
Solving Efficiency: Any configuration can be solved in 20 moves or fewer, as proven in 2010.
Representation Approaches
We can represent the Rubik's Cube using:

3D Array
1D Array
Bitboard

#Graph-Based Approach
The problem of solving the Rubik's Cube can be modeled as a graph where:

Each state of the cube is a node.
Each operation (move) transitions the cube from one state to another, akin to moving between nodes in a graph.

# Algorithms Overview
# 1. Depth-First Search (DFS)
DFS is a graph traversal algorithm that explores as far as possible along each branch before backtracking. It uses a stack (either explicitly or via recursion) to remember which nodes to explore next.

 Characteristics:</br>
Space Efficient: Requires less memory compared to BFS since it only stores nodes along the current path.
Not Optimal: DFS does not guarantee the shortest path to the goal.
Time Complexity: O(b^d), where b is the branching factor and d is the depth of the solution.
Can Get Stuck: It may get trapped in deep paths or loops without reaching the goal.
# 2. Breadth-First Search (BFS)
BFS is a graph traversal algorithm that explores all the nodes at the present depth level before moving on to the nodes at the next depth level. It uses a queue to keep track of the nodes that need to be explored.

Characteristics:</br>
Optimal: BFS guarantees the shortest path in terms of the number of edges.
Space Complexity: It requires more memory as it stores all the child pointers at a given level.
Time Complexity: O(b^d), where b is the branching factor and d is the depth of the solution.
# 3. Iterative Deepening Depth-First Search (IDDFS)
IDDFS combines the depth-first search's space efficiency with the breadth-first search's optimal path-finding. It repeatedly performs depth-limited searches, increasing the depth limit with each iteration.

Characteristics:</br>
Space Efficient: Uses O(d) space, where d is the maximum depth.
Optimal: Like BFS, it finds the shortest path in terms of the number of edges.
Time Complexity: O(b^d), but each depth level is only searched once.
# 4. IDA Algorithm (Korf’s Algorithm)*
IDA* is an informed search algorithm that uses the principles of A* and IDDFS. It incorporates heuristics to guide the search, allowing it to find solutions more efficiently than IDDFS alone.

Characteristics:</br>
Optimal: Guarantees the shortest path to the goal state if the heuristic is admissible (never overestimates).
Space Efficient: Uses O(d) space, similar to IDDFS.
Time Complexity: Depends on the quality of the heuristic used.
