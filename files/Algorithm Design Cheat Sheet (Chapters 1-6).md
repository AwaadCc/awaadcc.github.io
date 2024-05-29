#  Algorithm Design Cheat Sheet (Chapters 1-6)

#### Chapter 1: Introduction
- **Algorithm**: A step-by-step procedure for solving a problem.
- **Basic Efficiency Classes**: Constant \(O(1)\), Logarithmic \(O(\log n)\), Linear \(O(n)\), Quadratic \(O(n^2)\), Cubic \(O(n^3)\), Exponential \(O(2^n)\).
- **Pseudocode**: A high-level description of an algorithm using structured language.
- **Data Structures**: Arrays, Linked Lists, Stacks, Queues.

#### Chapter 2: Fundamentals of the Analysis of Algorithm Efficiency
- **Big-O Notation**: Represents upper bound efficiency.
- **Omega (Ω) Notation**: Represents lower bound efficiency.
- **Theta (θ) Notation**: Represents tight bound efficiency.
- **Recurrence Relations**: Used to analyze recursive algorithms (e.g., Master Theorem).

#### Chapter 3: Brute Force
- **Selection Sort**: \(O(n^2)\) - Repeatedly selects the smallest element.
- **Bubble Sort**: \(O(n^2)\) - Repeatedly swaps adjacent elements.
- **Sequential Search**: \(O(n)\) - Searches element by element.
- **Exhaustive Search**: Tries all possibilities to find the solution.
- **Knapsack Problem**: Finds the most valuable subset of items fitting into a knapsack.

#### Chapter 4: Divide-and-Conquer
- **Merge Sort**: \(O(n \log n)\) - Recursively divides the array and merges sorted halves.
- **Quick Sort**: \(O(n \log n)\) average, \(O(n^2)\) worst - Uses partitioning to sort.
- **Binary Search**: \(O(\log n)\) - Divides the search interval in half.
- **Strassen’s Matrix Multiplication**: \(O(n^{\log_2 7})\) - More efficient matrix multiplication.
- **Recurrence Relations**: Used to determine the time complexity of divide-and-conquer algorithms.

#### Chapter 5: Decrease-and-Conquer
- **Insertion Sort**: \(O(n^2)\) - Builds the final sorted array one item at a time.
- **Topological Sorting**: Orders vertices in a directed acyclic graph (DAG).
- **Binary Search Trees**: Data structure for dynamic set operations.
- **Euclidean Algorithm**: \(O(\log \min(a, b))\) - Finds the greatest common divisor (gcd).

#### Chapter 6: Transform-and-Conquer
- **Presorting**: Sorting the input to simplify the problem.
  - **Examples**: Checking uniqueness, computing mode, searching.
- **Gaussian Elimination**: \(O(n^3)\) - Solves systems of linear equations by transforming to upper triangular form.
- **LU Decomposition**: Factorizes a matrix into a lower and upper triangular matrix.
- **Balanced Search Trees**: Maintain balanced properties for efficient operations.
  - **AVL Trees**: Balance factor is at most 1.
  - **2-3 Trees**: Nodes can have 2 or 3 children, ensuring balance.
- **Heaps and Heapsort**:
  - **Heap**: Binary tree with heap property (parental dominance).
  - **Heapsort**: \(O(n \log n)\) - Sorts by converting to a heap and repeatedly extracting the maximum.
- **Horner’s Rule**: Efficient polynomial evaluation \(O(n)\).
- **Binary Exponentiation**: Computes \(a^n\) in \(O(\log n)\).
- **Problem Reduction**: Reducing one problem to another with a known solution.
  - **Examples**: Least common multiple, counting paths in a graph, linear programming.

---

#### Key Algorithms and Their Complexities
- **Selection Sort**: \(O(n^2)\)
- **Bubble Sort**: \(O(n^2)\)
- **Merge Sort**: \(O(n \log n)\)
- **Quick Sort**: Average \(O(n \log n)\), Worst \(O(n^2)\)
- **Binary Search**: \(O(\log n)\)
- **Insertion Sort**: \(O(n^2)\)
- **Heapsort**: \(O(n \log n)\)
- **Gaussian Elimination**: \(O(n^3)\)
- **Binary Exponentiation**: \(O(\log n)\)

#### Fundamental Concepts
- **Big-O, Omega, Theta Notations**: For expressing algorithm efficiency.
- **Divide-and-Conquer**: Divide the problem into subproblems, solve them independently, and combine the results.
- **Decrease-and-Conquer**: Reduce the problem to a smaller instance and extend the solution.
- **Transform-and-Conquer**: Transform the problem or its instance for easier solving.

#### Problem-Solving Techniques
- **Brute Force**: Try all possibilities.
- **Divide-and-Conquer**: Break into subproblems, solve, and merge.
- **Decrease-and-Conquer**: Simplify the problem progressively.
- **Transform-and-Conquer**: Transform for a better approach.

Use this cheat sheet as a quick reference guide for fundamental algorithms and their efficiencies, as well as the techniques and concepts from chapters 1 to 6.