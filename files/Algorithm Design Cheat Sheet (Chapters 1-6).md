# Algorithm Design Cheat Sheet (Chapters 1-6)

## Chapter 1: Introduction
### Algorithm
- **Definition**: A step-by-step procedure for solving a problem or accomplishing a task.
- **Characteristics**: Well-defined, finite, and effective.

### Basic Efficiency Classes
- **Constant \(O(1)\)**: Execution time is constant, regardless of input size.
- **Logarithmic \(O(\log n)\)**: Execution time grows logarithmically with input size.
- **Linear \(O(n)\)**: Execution time grows linearly with input size.
- **Quadratic \(O(n^2)\)**: Execution time grows quadratically with input size.
- **Cubic \(O(n^3)\)**: Execution time grows cubically with input size.
- **Exponential \(O(2^n)\)**: Execution time doubles with each additional input element.

### Pseudocode
- **Definition**: A high-level description of an algorithm using structured language that resembles programming code.
- **Purpose**: To outline the algorithm's logic without focusing on syntax.

### Data Structures
- **Arrays**: Fixed-size collections of elements of the same type.
- **Linked Lists**: Collections of elements, each pointing to the next.
- **Stacks**: Last-In-First-Out (LIFO) data structure.
- **Queues**: First-In-First-Out (FIFO) data structure.

## Chapter 2: Fundamentals of the Analysis of Algorithm Efficiency
### Big-O Notation
- **Definition**: Represents the upper bound of an algorithm's running time, describing the worst-case scenario.
- **Example**: \(O(n)\) for linear time algorithms.

### Omega (Ω) Notation
- **Definition**: Represents the lower bound of an algorithm's running time, describing the best-case scenario.
- **Example**: \(\Omega(n)\) for linear time algorithms.

### Theta (θ) Notation
- **Definition**: Represents the tight bound of an algorithm's running time, describing both the upper and lower bounds.
- **Example**: \(\Theta(n)\) for linear time algorithms.

### Recurrence Relations
- **Definition**: Equations or inequalities that describe the running time of a recursive algorithm.
- **Master Theorem**: Provides a way to solve recurrence relations of the form \(T(n) = aT(n/b) + f(n)\).

## Chapter 3: Brute Force
### Selection Sort
- **Complexity**: \(O(n^2)\)
- **Description**: Repeatedly selects the smallest element from the unsorted portion and swaps it with the first unsorted element.

### Bubble Sort
- **Complexity**: \(O(n^2)\)
- **Description**: Repeatedly compares and swaps adjacent elements if they are in the wrong order.

### Sequential Search
- **Complexity**: \(O(n)\)
- **Description**: Searches for an element by checking each element in the sequence until the target is found or the sequence ends.

### Exhaustive Search
- **Description**: Tries all possible solutions to find the optimal one.
- **Examples**: Solving puzzles, generating permutations.

### Knapsack Problem
- **Description**: Finds the most valuable subset of items that fit into a knapsack of limited capacity.
- **Complexity**: \(O(2^n)\) for brute force solution.

## Chapter 4: Divide-and-Conquer
### Merge Sort
- **Complexity**: \(O(n \log n)\)
- **Description**: Recursively divides the array into halves, sorts each half, and merges the sorted halves.

### Quick Sort
- **Average Complexity**: \(O(n \log n)\)
- **Worst Complexity**: \(O(n^2)\)
- **Description**: Partitions the array into two parts, sorts them independently, and combines them.

### Binary Search
- **Complexity**: \(O(\log n)\)
- **Description**: Recursively divides the search interval in half to find the target element.

### Strassen’s Matrix Multiplication
- **Complexity**: \(O(n^{\log_2 7})\)
- **Description**: More efficient algorithm for multiplying matrices.

### Recurrence Relations
- **Purpose**: Used to determine the time complexity of divide-and-conquer algorithms.

## Chapter 5: Decrease-and-Conquer
### Insertion Sort
- **Complexity**: \(O(n^2)\)
- **Description**: Builds the final sorted array one item at a time by inserting each element into its correct position.

### Topological Sorting
- **Description**: Orders vertices in a directed acyclic graph (DAG) such that for every directed edge \(uv\), vertex \(u\) comes before \(v\).
- **Applications**: Scheduling tasks, resolving dependencies.

### Binary Search Trees (BST)
- **Description**: Data structure that maintains sorted order of elements, supporting dynamic set operations like insert, delete, and find.
- **Complexity**: Average \(O(\log n)\), Worst \(O(n)\).

### Euclidean Algorithm
- **Complexity**: \(O(\log \min(a, b))\)
- **Description**: Efficient algorithm for computing the greatest common divisor (gcd) of two numbers.

## Chapter 6: Transform-and-Conquer
### Presorting
- **Description**: Sorting the input to simplify problem-solving.
- **Applications**: Checking uniqueness, computing mode, efficient searching.

### Gaussian Elimination
- **Complexity**: \(O(n^3)\)
- **Description**: Solves systems of linear equations by transforming the matrix into upper triangular form.

### LU Decomposition
- **Description**: Factorizes a matrix into a lower triangular matrix \(L\) and an upper triangular matrix \(U\).
- **Applications**: Solving linear equations, inverting matrices.

### Balanced Search Trees
- **Description**: Trees that maintain a balanced structure for efficient operations.
  - **AVL Trees**: Balance factor (difference in heights of left and right subtrees) is at most 1.
  - **2-3 Trees**: Nodes can have 2 or 3 children, ensuring balanced tree height.

### Heaps and Heapsort
- **Heap**: A binary tree with the heap property (parental dominance).
- **Heapsort Complexity**: \(O(n \log n)\)
- **Description**: Sorts an array by converting it to a heap and repeatedly extracting the maximum element.

### Horner’s Rule
- **Complexity**: \(O(n)\)
- **Description**: Efficient algorithm for polynomial evaluation.

### Binary Exponentiation
- **Complexity**: \(O(\log n)\)
- **Description**: Efficiently computes \(a^n\) using exponentiation by squaring.

### Problem Reduction
- **Description**: Reducing one problem to another with a known solution.
- **Examples**: Least common multiple, counting paths in a graph, linear programming.

---

## Key Algorithms and Their Complexities
- **Selection Sort**: \(O(n^2)\)
- **Bubble Sort**: \(O(n^2)\)
- **Merge Sort**: \(O(n \log n)\)
- **Quick Sort**: Average \(O(n \log n)\), Worst \(O(n^2)\)
- **Binary Search**: \(O(\log n)\)
- **Insertion Sort**: \(O(n^2)\)
- **Heapsort**: \(O(n \log n)\)
- **Gaussian Elimination**: \(O(n^3)\)
- **Binary Exponentiation**: \(O(\log n)\)

## Fundamental Concepts
- **Big-O, Omega, Theta Notations**: For expressing algorithm efficiency.
- **Divide-and-Conquer**: Divide the problem into subproblems, solve them independently, and combine the results.
- **Decrease-and-Conquer**: Reduce the problem to a smaller instance and extend the solution.
- **Transform-and-Conquer**: Transform the problem or its instance for easier solving.

## Problem-Solving Techniques
- **Brute Force**: Try all possibilities.
- **Divide-and-Conquer**: Break into subproblems, solve, and merge.
- **Decrease-and-Conquer**: Simplify the problem progressively.
- **Transform-and-Conquer**: Transform for a better approach.

Use this cheat sheet as a quick reference guide for fundamental algorithms and their efficiencies, as well as the techniques and concepts from chapters 1 to 6.
