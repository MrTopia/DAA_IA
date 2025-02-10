## **1. Fundamentals of Algorithms and Analysis of Algorithms**  

### **1. What is an algorithm?**  
An algorithm is a finite sequence of well-defined instructions that take an input and produce an output while solving a specific problem. It should be **unambiguous, efficient, and correct**. Algorithms are the foundation of computing and can be implemented in various programming languages.  

### **2. What are asymptotic notations?**  
Asymptotic notations describe the time or space complexity of an algorithm in terms of input size \( n \). The most commonly used notations are:  
- **Big-O (O):** Represents the upper bound (worst-case complexity). Example: O(n²) for Bubble Sort.  
- **Theta (Θ):** Represents a tight bound (average-case complexity). Example: Θ(n log n) for Merge Sort.  
- **Omega (Ω):** Represents the lower bound (best-case complexity). Example: Ω(n) for Insertion Sort in a sorted array.  

### **3. Explain growth rates with examples.**  
Growth rate describes how an algorithm's running time increases with input size. Examples include:  
- **Constant time (O(1)):** Accessing an element in an array.  
- **Logarithmic time (O(log n)):** Binary search, as it halves the search space at each step.  
- **Linear time (O(n)):** Traversing an array using a loop.  
- **Quadratic time (O(n²)):** Nested loops, such as in Bubble Sort.  
- **Exponential time (O(2ⁿ)):** Recursive Fibonacci calculation.  

### **4. Differentiate between worst-case and average-case analysis.**  
- **Worst-case analysis** considers the longest time an algorithm can take for any input of size \( n \), ensuring performance is predictable under maximum workload. Example: Quick Sort worst case is O(n²) when the pivot is the smallest/largest element.  
- **Average-case analysis** considers the expected runtime for a random input, giving a more realistic measure of efficiency. Example: Quick Sort's average case is O(n log n).  

### **5. How do control statements affect time complexity?**  
Control statements like loops and recursion significantly influence an algorithm’s complexity:  
- **Loops:** A single loop running \( n \) times results in O(n), while nested loops running \( n \times n \) times result in O(n²).  
- **Recursion:** If a recursive function calls itself twice per iteration, complexity often follows the recurrence relation \( T(n) = 2T(n/2) + O(n) \), which resolves to O(n log n) using the **Master theorem**.  

### **6. Solve T(n) = 2T(n/2) + O(n) using the Master theorem.**  
Applying the Master theorem:  
- \( a = 2 \), \( b = 2 \), and \( f(n) = O(n) \).  
- Since log₂(2) = 1 and \( f(n) \) is O(n), the complexity is **O(n log n)**, which is common for sorting algorithms like Merge Sort and Quick Sort (average case).  

---

## **2. Divide and Conquer Algorithms**  

### **7. What is divide and conquer?**  
Divide and conquer is an algorithm design paradigm where a problem is broken into smaller subproblems, solved recursively, and combined to get the final solution. Examples include Merge Sort, Quick Sort, and Binary Search.  

### **8. Explain Quick Sort with its worst and average-case complexity.**  
Quick Sort selects a **pivot** and partitions the array such that elements smaller than the pivot go to the left, and larger ones go to the right.  
- **Worst case (O(n²))**: If the pivot is always the smallest or largest element, leading to unbalanced partitions.  
- **Average case (O(n log n))**: When partitions are balanced, leading to efficient sorting.  

### **9. What is Merge Sort, and what is its time complexity?**  
Merge Sort divides the array into two halves, sorts each recursively, and merges them. It always runs in **O(n log n)** time as it divides the array in **log n** steps and takes **O(n)** time to merge.  

### **10. Explain Strassen’s Matrix Multiplication.**  
Strassen’s algorithm optimizes matrix multiplication by reducing the number of multiplications from **O(n³)** to **O(n².81)**. Instead of performing 8 multiplications for two **n × n** matrices, it performs only 7, reducing the computational cost.  

### **11. Explain Binary Search and its time complexity.**  
Binary Search efficiently finds an element in a sorted array by repeatedly halving the search space. It has a worst-case time complexity of **O(log n)** since it reduces the problem size exponentially.  

### **12. How do you find the maximum and minimum in an array using divide and conquer?**  
Instead of scanning the entire array (O(n)), we:  
1. Divide the array into two halves.  
2. Recursively find the max and min in each half.  
3. Compare results from both halves, reducing comparisons to **O(n)**.  

---

## **3. Greedy Algorithms**  

### **13. What is a greedy algorithm?**  
A greedy algorithm makes the best choice at each step, hoping to achieve a global optimum. However, it does not always provide an optimal solution for all problems.  

### **14. Explain Kruskal’s algorithm for Minimum Spanning Tree (MST).**  
Kruskal’s algorithm sorts all edges by weight and adds the smallest edge to the MST if it does not create a cycle. It runs in **O(E log E)** due to sorting and uses the **Union-Find** data structure to detect cycles.  

### **15. Explain Prim’s algorithm for MST.**  
Prim’s algorithm grows the MST starting from one vertex by repeatedly adding the smallest edge connecting the tree to an unvisited vertex. It runs in **O(E log V)** using a **priority queue**.  

### **16. How does Dijkstra’s algorithm work for finding the shortest path?**  
Dijkstra’s algorithm finds the shortest path from a source vertex to all other vertices in a weighted graph by:  
1. Initializing distances to infinity except for the source (0).  
2. Picking the vertex with the smallest known distance.  
3. Updating neighbors if a shorter path is found.  
4. Repeating until all nodes are visited.  
It runs in **O((V + E) log V)** using a priority queue.  

### **17. What is the fractional Knapsack problem?**  
A greedy approach to the Knapsack problem where items can be divided. We take items with the **highest value-to-weight ratio** until the knapsack is full, achieving an **optimal O(n log n) solution**.  

### **18. What is Huffman coding?**  
A greedy algorithm for data compression that assigns shorter binary codes to more frequent symbols. It builds a **Huffman Tree**, ensuring **prefix-free encoding**, reducing storage space. Runs in **O(n log n)**.  

## **4. Dynamic Programming (DP)**  

### **19. What is dynamic programming, and how does it differ from divide and conquer?**  
Dynamic programming (DP) is an optimization technique used to solve problems by breaking them into overlapping subproblems and storing solutions to avoid redundant computations.  
- **Difference from divide and conquer:**  
  - DP solves overlapping subproblems and stores results (memoization).  
  - Divide and conquer solves independent subproblems recursively.  
  - Example: Merge Sort (divide and conquer) vs. Fibonacci sequence (DP).  

### **20. What is the principle of optimality in DP?**  
The principle states that an optimal solution to a problem contains optimal solutions to its subproblems.  
Example: The **Shortest Path Problem** follows this principle, as any segment of an optimal path is also optimal.  

### **21. Solve Fibonacci numbers using DP.**  
A recursive Fibonacci function has **exponential O(2ⁿ) complexity**. Using DP, we store computed values:  

**Top-down (memoization):**  
```cpp
int fib(int n, vector<int>& dp) {
  if (n <= 1) return n;
  if (dp[n] != -1) return dp[n];
  return dp[n] = fib(n - 1, dp) + fib(n - 2, dp);
}
```  
**Bottom-up (tabulation) reduces time to O(n):**  
```cpp
int fib(int n) {
  vector<int> dp(n+1);
  dp[0] = 0, dp[1] = 1;
  for (int i = 2; i <= n; i++)
    dp[i] = dp[i-1] + dp[i-2];
  return dp[n];
}
```  

### **22. Explain Warshall’s Algorithm for the transitive closure of a graph.**  
Warshall’s algorithm determines if there is a path between two vertices in a graph.  
- Uses a **Boolean adjacency matrix** and updates paths iteratively.  
- Runs in **O(V³)** time complexity.  

### **23. Explain Floyd-Warshall’s Algorithm for shortest paths.**  
Floyd-Warshall finds shortest paths between all pairs of vertices in a weighted graph.  
- Uses a **distance matrix**, updating values iteratively.  
- Runs in **O(V³)**, useful for dense graphs.  

### **24. Explain the Matrix Chain Multiplication problem.**  
Given matrices \( A_1, A_2, ..., A_n \), we find the optimal way to parenthesize them to minimize computations.  
- Uses DP with the recurrence:  
  \[
  dp[i][j] = \min(dp[i][k] + dp[k+1][j] + A[i-1] \times A[k] \times A[j])
  \]
- Runs in **O(n³)**.  

### **25. What is the Longest Common Subsequence (LCS) problem?**  
LCS finds the longest sequence that appears in order in both strings.  
- DP formula:  
  \[
  dp[i][j] =
  \begin{cases}
    dp[i-1][j-1] + 1, & \text{if } s_1[i] == s_2[j] \\
    \max(dp[i-1][j], dp[i][j-1]), & \text{otherwise}
  \end{cases}
  \]
- Runs in **O(mn)**.  

### **26. What is the Optimal Binary Search Tree (OBST) problem?**  
OBST minimizes the search cost in a BST when keys have different access probabilities.  
- DP formula considers subtree costs and search frequencies.  
- Runs in **O(n³)**.  

---

## **5. Graph Algorithms**  

### **27. What are graph traversal techniques?**  
Graph traversal methods include:  
- **Depth First Search (DFS):** Uses recursion or stack, explores as deep as possible before backtracking.  
- **Breadth First Search (BFS):** Uses a queue, explores all neighbors before moving to the next level.  

### **28. Implement BFS in a graph.**  
```cpp
void BFS(int start, vector<int> adj[], int V) {
  queue<int> q;
  vector<bool> visited(V, false);
  q.push(start);
  visited[start] = true;
  while (!q.empty()) {
    int node = q.front(); q.pop();
    cout << node << " ";
    for (int neighbor : adj[node])
      if (!visited[neighbor]) {
        visited[neighbor] = true;
        q.push(neighbor);
      }
  }
}
```  

### **29. Implement DFS in a graph.**  
```cpp
void DFS(int node, vector<int> adj[], vector<bool>& visited) {
  visited[node] = true;
  cout << node << " ";
  for (int neighbor : adj[node])
    if (!visited[neighbor]) DFS(neighbor, adj, visited);
}
```  

---

## **6. Backtracking and Branch & Bound**  

### **30. Solve the 0/1 Knapsack Problem using Branch & Bound.**  
- Unlike DP, **Branch & Bound** prunes branches where the weight exceeds capacity.  
- Uses a priority queue to explore promising paths first.  
- Runs in **O(2ⁿ)** in the worst case.  

### **31. Explain the Eight Queens problem using backtracking.**  
The Eight Queens problem places 8 queens on an 8x8 chessboard without attacking each other.  
- Recursively places queens, backtracking when a conflict arises.  
- Runs in **O(n!)**.  

### **32. What is the Travelling Salesman Problem (TSP)?**  
TSP finds the shortest cycle visiting all cities exactly once.  
- **Backtracking:** Tries all permutations (O(n!)).  
- **Branch & Bound:** Uses cost reduction techniques for better pruning.  

---

## **7. String Matching Algorithms**  

### **33. What is the Naive String Matching algorithm?**  
- Compares the pattern to each substring of the text.  
- Runs in **O(nm)** worst case, where \( n \) is text length and \( m \) is pattern length.  

### **34. Explain the Rabin-Karp algorithm.**  
- Uses **hashing** to compare substrings efficiently.  
- Rolling hash function reduces comparisons.  
- Average complexity: **O(n + m)**.  

### **35. Explain the Knuth-Morris-Pratt (KMP) algorithm.**  
- Builds a **prefix function** to avoid unnecessary comparisons.  
- Runs in **O(n + m)** time.  

---

## **8. Complexity Theory**  

### **36. What are P and NP problems?**  
- **P (Polynomial time):** Problems solvable in polynomial time (e.g., Sorting, Shortest Path).  
- **NP (Nondeterministic Polynomial time):** Problems where solutions can be **verified** in polynomial time but may take **exponential time** to solve (e.g., TSP, Knapsack).  

### **37. What is NP-Completeness?**  
A problem is **NP-complete** if:  
1. It is in NP.  
2. Any NP problem can be **reduced** to it in polynomial time.  
Example: **3-SAT, Traveling Salesman Problem**.  

### **38. What is an NP-Hard problem?**  
NP-Hard problems are at least as hard as NP problems but do not have to be in NP.  
Example: **Halting Problem** (not verifiable in polynomial time).  

### **39. What is polynomial reduction?**  
- Converts one problem to another in **polynomial time**.  
- Used to prove **NP-Completeness**.  
Example: **SAT can be reduced to 3-SAT**.
