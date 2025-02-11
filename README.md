## **1. Fundamentals of Algorithms and Analysis of Algorithms**  

### **1. What is an algorithm?**  
An algorithm is a finite sequence of well-defined instructions that take an input and produce an output while solving a specific problem. It should be **unambiguous, efficient, and correct**. Algorithms are the foundation of computing and can be implemented in various programming languages.  

### **2. What are asymptotic notations?**  
Asymptotic notations describe the time or space complexity of an algorithm in terms of input size \( n \). The most commonly used notations are:  
- **Big-O (O):** Represents the upper bound (worst-case complexity). Example: O(n²) for Bubble Sort.  
- **Theta (Θ):** Represents a tight bound (average-case complexity). Example: Θ(n log n) for Merge Sort.  
- **Omega (Ω):** Represents the lower bound (best-case complexity). Example: Ω(n) for Insertion Sort in a sorted array.  

### **3. Explain growth rates with examples.**  
Time complexity measures the **growth rate** of an algorithm's execution time **relative to input size (n)**. The major types are:  

### **1. Constant Time – \( O(1) \)**
- **Execution time does not depend on input size.**  
- The algorithm runs in a **fixed number of steps** regardless of \( n \).  

**Example:**  
```cpp
int firstElement(int arr[]) {
    return arr[0];  // Always executes once
}
```
Even if the array has 1000 elements, the function runs in **constant time**.  

---

### **2. Logarithmic Time – \( O(\log n) \)**
- The algorithm **reduces the problem size** in each step (e.g., halves it).  
- Found in **binary search, tree operations**.  

**Example: Binary Search**  
```cpp
int binarySearch(int arr[], int n, int key) {
    int left = 0, right = n - 1;
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == key) return mid;
        else if (arr[mid] < key) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}
```
Each iteration halves the search space, leading to **\( O(\log n) \) complexity**.  

---

### **3. Linear Time – \( O(n) \)**
- Execution time **increases proportionally** with input size.  
- Common in **simple loops**.  

**Example: Finding Maximum in an Array**  
```cpp
int findMax(int arr[], int n) {
    int maxVal = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] > maxVal) maxVal = arr[i];
    }
    return maxVal;
}
```
For an array of size **1000**, it runs **1000 times**, making it **\( O(n) \)**.  

---

### **4. Linearithmic Time – \( O(n \log n) \)**
- Found in **efficient sorting algorithms (Merge Sort, QuickSort, Heap Sort)**.  
- Due to **recursive division** (log factor) and **merging** (linear factor).  

**Example: Merge Sort**  
```cpp
void mergeSort(int arr[], int left, int right) {
    if (left >= right) return;
    int mid = left + (right - left) / 2;
    mergeSort(arr, left, mid);
    mergeSort(arr, mid + 1, right);
    merge(arr, left, mid, right);
}
```
Each division takes **\( O(\log n) \)** time, and merging takes **\( O(n) \)**, leading to **\( O(n \log n) \)**.  

---

### **5. Quadratic Time – \( O(n^2) \)**
- Found in **nested loops**, common in brute-force algorithms.  
- **Slow for large inputs**.  

**Example: Bubble Sort**  
```cpp
void bubbleSort(int arr[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) swap(arr[j], arr[j + 1]);
        }
    }
}
```
Each element is compared with every other element, making it **\( O(n^2) \)**.  

---

### **6. Cubic Time – \( O(n^3) \)**
- Appears in **triple nested loops**.  
- Found in **matrix multiplication, Floyd-Warshall algorithm**.  

**Example: Floyd-Warshall Algorithm for Shortest Paths**  
```cpp
for (int k = 0; k < n; k++) {
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j]);
        }
    }
}
```
For **\( n = 100 \)**, this runs **1,000,000 times**!  

---

### **7. Exponential Time – \( O(2^n) \)**
- Found in **recursive algorithms** like Fibonacci, Subset Problems.  
- **Impractical for large \( n \)**.  

**Example: Recursive Fibonacci**  
```cpp
int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```
Each call branches into two more calls, leading to **exponential growth**.  

---

### **8. Factorial Time – \( O(n!) \)**
- Found in **brute-force combinatorial problems** (TSP, Permutations).  
- **Unusable for large inputs**.  

**Example: Generating All Permutations**  
```cpp
void permute(string s, int l, int r) {
    if (l == r) cout << s << endl;
    else {
        for (int i = l; i <= r; i++) {
            swap(s[l], s[i]);
            permute(s, l + 1, r);
            swap(s[l], s[i]);
        }
    }
}
```
For **\( n = 5 \)**, it runs **\( 5! = 120 \)** times!  

---

### **Summary Table**  

| Complexity  | Name                 | Example Algorithm             | Growth Rate |
|------------|----------------------|------------------------------|------------|
| \( O(1) \)   | Constant Time        | Accessing an array element   | Same time always |
| \( O(\log n) \)  | Logarithmic Time    | Binary Search                | Grows slowly |
| \( O(n) \)   | Linear Time         | Finding Max in an array      | Doubles if \( n \) doubles |
| \( O(n \log n) \) | Linearithmic Time   | Merge Sort                   | Slightly faster than \( O(n^2) \) |
| \( O(n^2) \) | Quadratic Time      | Bubble Sort                   | Slow for large \( n \) |
| \( O(n^3) \) | Cubic Time          | Floyd-Warshall Algorithm      | Even slower |
| \( O(2^n) \) | Exponential Time    | Fibonacci (Recursive)        | Doubles with each increment |
| \( O(n!) \)  | Factorial Time      | Generating all permutations  | Unmanageable for large \( n \) |

---

### **Conclusion**
- **Best cases:** \( O(1) \), \( O(\log n) \), \( O(n) \), \( O(n \log n) \).  
- **Manageable but slow:** \( O(n^2) \), \( O(n^3) \).  
- **Unusable for large inputs:** \( O(2^n) \), \( O(n!) \).  

For **efficient algorithms**, aim for at most **\( O(n \log n) \)**.  

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
Dynamic Programming (DP) is an optimization technique used to solve problems by breaking them into **overlapping subproblems** and storing their solutions to avoid redundant computations. It is primarily used for problems with **optimal substructure**, meaning the solution to a larger problem is built using solutions to its subproblems.  

**Difference from Divide and Conquer:**  
- **DP:** Solves overlapping subproblems and stores solutions (memoization/tabulation).  
- **Divide and Conquer:** Solves independent subproblems and combines results (e.g., Merge Sort).  

**Example:**  
- **Fibonacci Sequence (DP):** Stores computed values to prevent repeated calculations.  
- **Merge Sort (Divide and Conquer):** Recursively divides the array and merges sorted halves.  

---

### **20. What is the principle of optimality in dynamic programming?**  
The **Principle of Optimality** states that an optimal solution to a problem contains optimal solutions to its subproblems. In other words, if a problem can be broken down into subproblems, solving each subproblem optimally ensures an optimal overall solution.  

**Example:**  
In the **Shortest Path Problem**, the shortest route from A to C via B ensures that the path from A to B and B to C are also optimal. This allows dynamic programming algorithms like **Floyd-Warshall** and **Dijkstra’s algorithm** to work efficiently.  

---

### **21. Solve Fibonacci numbers using dynamic programming.**  
The Fibonacci sequence follows the recurrence relation:  
\[
F(n) = F(n-1) + F(n-2), \quad \text{where } F(0) = 0, \, F(1) = 1
\]  

**Naive Recursion (Exponential Time Complexity O(2ⁿ))**  
```cpp
int fib(int n) {
    if (n <= 1) return n;
    return fib(n-1) + fib(n-2);
}
```  
This approach is inefficient due to repeated calculations.  

**Dynamic Programming (Efficient O(n) Solution)**  
**Memoization (Top-Down Approach)**  
```cpp
int fib(int n, vector<int>& dp) {
    if (n <= 1) return n;
    if (dp[n] != -1) return dp[n];
    return dp[n] = fib(n - 1, dp) + fib(n - 2, dp);
}
```  
**Tabulation (Bottom-Up Approach)**  
```cpp
int fib(int n) {
    vector<int> dp(n+1);
    dp[0] = 0, dp[1] = 1;
    for (int i = 2; i <= n; i++)
        dp[i] = dp[i-1] + dp[i-2];
    return dp[n];
}
```  
This avoids redundant computations, making the algorithm efficient.  

---

### **22. Explain Warshall’s Algorithm for transitive closure of a graph.**  
Warshall’s Algorithm is used to determine if there is a **path between every pair of vertices** in a directed graph. It constructs a **Boolean adjacency matrix**, where `1` represents a path exists and `0` represents no path.  

**Algorithm:**  
1. Initialize an adjacency matrix **A**, where `A[i][j] = 1` if there is a direct edge from vertex `i` to `j`, otherwise `0`.  
2. For each intermediate vertex `k`, update `A[i][j]` as:  
   \[
   A[i][j] = A[i][j] \lor (A[i][k] \land A[k][j])
   \]  
3. After **V** iterations (where V is the number of vertices), the matrix shows whether a path exists between any two vertices.  

**Time Complexity:** \( O(V^3) \)  

---

### **23. Explain Floyd-Warshall’s Algorithm for shortest paths.**  
Floyd-Warshall finds the shortest path between **all pairs of vertices** in a weighted graph.  

**Algorithm Steps:**  
1. Create a **distance matrix** `D[i][j]`, where `D[i][j]` represents the shortest distance from vertex `i` to `j`.  
2. Initialize `D[i][j]` with direct edge weights (or `∞` if no edge exists).  
3. For each intermediate vertex `k`, update distances using:  
   \[
   D[i][j] = \min(D[i][j], D[i][k] + D[k][j])
   \]  
4. After **V** iterations, `D[i][j]` contains the shortest distance between all vertex pairs.  

**Time Complexity:** \( O(V^3) \)  

---

### **24. Explain the Matrix Chain Multiplication problem.**  
Given matrices **A₁, A₂, ..., Aₙ**, we aim to parenthesize them optimally to minimize scalar multiplications.  

**Recurrence Relation:**  
\[
dp[i][j] = \min_{i \leq k < j} (dp[i][k] + dp[k+1][j] + A[i-1] \times A[k] \times A[j])
\]  
This ensures the multiplication sequence is optimized.  

**Time Complexity:** \( O(n^3) \)  

---

### **25. What is the Longest Common Subsequence (LCS) problem?**  
LCS finds the longest subsequence appearing in both strings while maintaining order.  

**Recurrence Relation:**  
\[
dp[i][j] =
\begin{cases}
    dp[i-1][j-1] + 1, & \text{if } s_1[i] == s_2[j] \\
    \max(dp[i-1][j], dp[i][j-1]), & \text{otherwise}
\end{cases}
\]  
Example:  
- Input: `X = "ABCBDAB"`, `Y = "BDCAB"`  
- LCS: `"BCAB"`  

**Time Complexity:** \( O(mn) \)  

---

### **26. What is the Optimal Binary Search Tree (OBST) problem?**  
OBST minimizes search cost for a Binary Search Tree (BST) when keys have **different access probabilities**.  

**Recurrence Relation:**  
\[
dp[i][j] = \min_{i \leq k \leq j} (dp[i][k-1] + dp[k+1][j] + W(i,j))
\]  
where **W(i, j)** is the sum of probabilities.  

**Time Complexity:** \( O(n^3) \)  

---

### **27. What are graph traversal techniques?**  
Graph traversal involves systematically visiting vertices. Two main techniques are:  
1. **Depth-First Search (DFS):**  
   - Uses a stack (or recursion).  
   - Explores as deep as possible before backtracking.  
   - **Time Complexity:** \( O(V + E) \)  

2. **Breadth-First Search (BFS):**  
   - Uses a queue.  
   - Explores all neighbors before moving deeper.  
   - **Time Complexity:** \( O(V + E) \)  

---

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



## **5. Backtracking and Branch & Bound**  

### **29. What is the 0/1 Knapsack Problem, and how is it solved using backtracking?**  
The **0/1 Knapsack Problem** is an optimization problem where a thief must maximize the total value of items in a **knapsack of limited capacity**. Each item has a weight and value, and it can either be **taken entirely (1) or left (0)**—hence the name **0/1 Knapsack**.  

**Backtracking Approach:**  
- Explore all possible subsets of items.
- Maintain a **current weight and value**.
- If adding an item exceeds the knapsack’s capacity, **backtrack** to try a different subset.  
- Use **pruning** to avoid unnecessary computations.

**Time Complexity:** \( O(2^n) \) (Exponential).  

---

### **30. Explain the Eight Queens Problem and its solution using backtracking.**  
The **Eight Queens Problem** requires placing 8 queens on an **8×8 chessboard** such that **no two queens attack each other**.  

**Backtracking Solution:**  
1. Place queens **one by one** in columns.
2. For each row, check if placing a queen **leads to conflicts**.
3. If it’s safe, move to the next column.
4. If a conflict arises, **backtrack** and try another row.  

**Time Complexity:** \( O(n!) \).  

---

### **31. What is the Traveling Salesman Problem (TSP), and how is it solved using Branch & Bound?**  
The **TSP** involves finding the shortest tour that visits each city exactly once and returns to the starting point.  

**Branch & Bound Approach:**  
1. Start from a city and explore all possible routes.
2. Maintain a **cost matrix** to track travel costs.
3. Use **bounding functions** to eliminate unpromising routes.
4. The lowest-cost complete tour is the optimal solution.  

**Time Complexity:** \( O(n!) \) (Exact), \( O(n^2 2^n) \) (Held-Karp DP).  

---

## **6. String Matching Algorithms**  

### **32. What is the Naïve String Matching Algorithm?**  
The **Naïve Algorithm** checks for a pattern **P** in a text **T** by sliding **P** one character at a time over **T** and checking for a match.  

**Algorithm Steps:**  
1. Compare **P** with a substring of **T** at each position.  
2. If a match is found, return the index.  
3. Otherwise, shift **P** one position to the right and repeat.  

**Time Complexity:** \( O(mn) \) (Worst case).  

---

### **33. Explain the Rabin-Karp Algorithm and its advantages.**  
Rabin-Karp uses **hashing** to find patterns efficiently.  

**Algorithm Steps:**  
1. Compute a **hash value** for the pattern **P** and the first substring of **T**.  
2. Slide **P** across **T** and **compare hash values** instead of characters.  
3. If hash values match, perform a **character-wise check**.  

**Advantages:**  
- Efficient for multiple pattern matching.  
- Average case: \( O(n) \).  
- Worst case (hash collisions): \( O(mn) \).  

---

### **34. Explain the Knuth-Morris-Pratt (KMP) Algorithm.**  
KMP improves **Naïve Matching** by using a **precomputed prefix table** to avoid redundant comparisons.  

**Algorithm Steps:**  
1. Build a **Longest Prefix Suffix (LPS) table**.  
2. Compare **P** and **T** using the LPS table to determine how much to shift.  

**Time Complexity:** \( O(n + m) \).  

---

## **7. Complexity Theory**  

### **35. What are P and NP problems?**  
- **P (Polynomial Time):** Problems solvable in polynomial time (\( O(n^k) \)). Example: **Sorting, Dijkstra’s algorithm**.  
- **NP (Nondeterministic Polynomial Time):** Problems where a **solution can be verified** in polynomial time. Example: **TSP, 0/1 Knapsack**.  

---

### **36. What are NP-Complete Problems? Give examples.**  
NP-Complete problems are **both NP and NP-Hard**—meaning:  
- Finding a solution is **as hard as verifying it**.  
- If an **efficient solution** exists for one NP-Complete problem, all NP problems can be solved efficiently.  

**Examples:**  
1. **Traveling Salesman Problem (TSP)**  
2. **Hamiltonian Path**  
3. **Subset Sum Problem**  

---

### **37. What are NP-Hard problems? How do they differ from NP-Complete?**  
**NP-Hard** problems are **at least as hard as NP problems**, but they may **not be in NP** (i.e., they may not have verifiable solutions in polynomial time).  

**Difference from NP-Complete:**  
- NP-Complete: Must be **in NP** and **as hard as NP**.  
- NP-Hard: Can be **harder than NP**, even unsolvable in polynomial time.  

**Example:** **Halting Problem** (undecidable).  

---

### **38. What is Polynomial Reduction?**  
Polynomial Reduction transforms one problem **A** into another problem **B** in polynomial time, proving that **B** is at least as hard as **A**.  

Example:  
To show **SAT (Boolean Satisfiability) is NP-Complete**, we **reduce** every NP problem to SAT.  

---

### **39. Why is the P vs. NP problem important?**  
If \( P = NP \), then all NP problems can be solved in polynomial time, revolutionizing fields like **cryptography, AI, and optimization**. However, this remains an **unsolved problem** in computer science.  

---

## **Final Set of Questions**  

### **40. What is Asymptotic Notation, and why is it used?**  
Asymptotic Notation describes the **growth rate of an algorithm’s runtime** as input size increases.  

**Types:**  
- **Big-O (O):** Upper bound (worst-case).  
- **Theta (Θ):** Tight bound (average case).  
- **Omega (Ω):** Lower bound (best case).  

Used for comparing algorithms **independently of hardware or implementation details**.  

---

### **41. What is the Master’s Theorem, and how is it used?**  
The **Master’s Theorem** provides a shortcut for solving **divide-and-conquer** recurrence relations of the form:  
\[
T(n) = aT(n/b) + O(n^d)
\]  

**Cases:**  
1. \( d > \log_b a \) → \( O(n^d) \)  
2. \( d = \log_b a \) → \( O(n^d \log n) \)  
3. \( d < \log_b a \) → \( O(n^{\log_b a}) \)  

**Example:** Merge Sort \( T(n) = 2T(n/2) + O(n) \) → \( O(n \log n) \).  

---

### **42. What is Strassen’s Matrix Multiplication?**  
Strassen’s Algorithm improves matrix multiplication from **\( O(n^3) \) to \( O(n^{2.81}) \)** using divide and conquer.  

**Algorithm Steps:**  
1. Divide matrices into **4 submatrices**.  
2. Compute **7 products instead of 8**.  
3. Combine results to get the final matrix.  

Used in **image processing, scientific computing**.  

---

### **43. What is Huffman Coding, and why is it used?**  
Huffman Coding is a **greedy algorithm** for data compression.  

**Steps:**  
1. Build a **frequency table**.  
2. Create a **Huffman tree** (lower frequency → deeper nodes).  
3. Encode data using **variable-length codes**.  

**Example:**  
Text: `AAABBBC` → Encoded: `1101100110` (using shorter codes for frequent characters).  


