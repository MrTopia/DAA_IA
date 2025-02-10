### **1. Fundamentals of Algorithms and Analysis of Algorithms**  

**1. What is an algorithm?**  
An algorithm is a step-by-step set of instructions designed to perform a specific task or solve a problem. It must be finite, well-defined, and effective.  

**2. What are asymptotic notations?**  
Asymptotic notations describe how the running time or space requirements of an algorithm grow with input size. The most common ones are:  
- **Big O (O)**: Upper bound (worst-case complexity)  
- **Theta (Θ)**: Tight bound (average-case complexity)  
- **Omega (Ω)**: Lower bound (best-case complexity)  

**3. What is the growth rate of an algorithm?**  
Growth rate indicates how an algorithm's performance scales with increasing input size. It helps in comparing algorithms in terms of efficiency.  

**4. List common growth rates with examples.**  
- **Constant (O(1))** → Accessing an element in an array.  
- **Logarithmic (O(log n))** → Binary search.  
- **Linear (O(n))** → Traversing an array.  
- **Polynomial (O(n²))** → Bubble sort, Insertion sort.  
- **Exponential (O(2ⁿ))** → Recursive Fibonacci calculation.  

**5. Differentiate between worst-case and average-case analysis.**  
- **Worst-case**: The maximum time an algorithm takes for any input of size \( n \).  
- **Average-case**: The expected time an algorithm takes for random inputs of size \( n \).  

**6. How do control statements affect complexity?**  
- **Loops**: Increase time complexity based on iterations (e.g., O(n) for a single loop, O(n²) for nested loops).  
- **Recursion**: Affects complexity based on recurrence relations.  

**7. Solve T(n) = 2T(n/2) + O(n) using Master’s theorem.**  
Using the Master theorem:  
- a = 2, b = 2, f(n) = O(n)  
- Since log₂(2) = 1 and f(n) = O(n), the complexity is **O(n log n)**.  

---

### **2. Divide and Conquer Algorithms**  

**8. What is divide and conquer?**  
A problem-solving technique that breaks a problem into smaller subproblems, solves them recursively, and combines the results.  

**9. Explain the worst-case complexity of Quick Sort.**  
Occurs when the pivot is always the smallest or largest element, leading to O(n²) time complexity.  

**10. Explain the average-case complexity of Quick Sort.**  
On average, the partitions are balanced, and the algorithm runs in O(n log n) time.  

**11. What is the time complexity of Merge Sort?**  
Merge Sort always runs in **O(n log n)** because it divides the array into halves recursively and merges them.  

**12. What is Strassen’s matrix multiplication algorithm?**  
A divide-and-conquer algorithm that multiplies two n × n matrices in **O(n^2.81)**, faster than the traditional **O(n³)** approach.  

**13. What is the best-case complexity of Binary Search?**  
O(1), when the middle element is the target.  

**14. What is the worst-case complexity of Binary Search?**  
O(log n), when searching in a sorted list without finding the element.  

**15. How do you find the maximum and minimum in an array using divide and conquer?**  
By dividing the array recursively, we reduce the number of comparisons from 2n-2 (brute force) to **O(n)**.  

---

### **3. Greedy Algorithms**  

**16. What are greedy algorithms?**  
Algorithms that make locally optimal choices at each step, hoping to achieve a global optimum.  

**17. Explain Kruskal’s algorithm.**  
A greedy algorithm for finding the **Minimum Spanning Tree (MST)** by sorting edges in increasing order and adding them if they don't form a cycle.  

**18. Explain Prim’s algorithm.**  
A greedy algorithm that starts with one node and grows the MST by adding the smallest edge that connects to an unvisited node.  

**19. What is Dijkstra’s algorithm used for?**  
It finds the **shortest path** from a single source vertex in a weighted graph using a priority queue.  

**20. Explain the Knapsack problem in greedy approach.**  
- The **Fractional Knapsack Problem** allows dividing items, so selecting items with the highest value-to-weight ratio gives the optimal solution.  

**21. What is Huffman coding?**  
A greedy algorithm for data compression that assigns shorter binary codes to more frequent symbols.  

---

### **4. Dynamic Programming**  

**22. What is dynamic programming?**  
A technique that solves problems by breaking them into subproblems, solving each once, and storing results to avoid recomputation.  

**23. State the Principle of Optimality.**  
An optimal solution contains optimal solutions to its subproblems.  

**24. What is the complexity of computing Fibonacci numbers using DP?**  
O(n) using memoization or tabulation instead of O(2ⁿ) in naive recursion.  

**25. What is Warshall’s algorithm used for?**  
Finding the **transitive closure** of a graph (whether a path exists between two vertices).  

**26. What is Floyd’s algorithm used for?**  
Finding the **all-pairs shortest path** using dynamic programming in O(n³).  

**27. What is the complexity of matrix chain multiplication using DP?**  
O(n³), as it considers all possible ways to multiply matrices for the minimum number of operations.  

**28. Explain the Longest Common Subsequence (LCS) problem.**  
Finds the longest sequence common to two given sequences in O(mn) time using dynamic programming.  

**29. What is an Optimal Binary Search Tree?**  
A BST that minimizes search costs based on access probabilities.  

---

### **5. Graph Algorithms**  

**30. Differentiate between DFS and BFS.**  
- **DFS**: Uses a **stack**, explores deep paths first.  
- **BFS**: Uses a **queue**, explores level by level.  

**31. What is the time complexity of DFS and BFS?**  
Both run in **O(V + E)**.  

---

### **6. Backtracking and Branch & Bound**  

**32. What is backtracking?**  
A recursive algorithm that explores all solutions and backtracks if a solution is invalid.  

**33. What is the 0/1 Knapsack problem?**  
A problem where items can't be divided, solved using dynamic programming or backtracking.  

**34. What is the Eight Queens problem?**  
A backtracking problem of placing 8 queens on a chessboard so that no two attack each other.  

**35. What is the Travelling Salesman Problem (TSP)?**  
An **NP-hard** problem of finding the shortest tour visiting all cities exactly once.  

---

### **7. String Matching Algorithms**  

**36. What is the naive string matching algorithm?**  
Checks all possible positions, leading to **O(mn)** complexity.  

**37. What is the Rabin-Karp algorithm?**  
Uses hashing for faster search, with an average complexity of **O(n + m)**.  

**38. What is the complexity of the KMP algorithm?**  
O(n + m) due to its preprocessing step using a prefix table.  

---

### **8. Complexity Theory**  

**39. What is P?**  
Class of problems solvable in polynomial time.  

**40. What is NP?**  
Class of problems where solutions can be verified in polynomial time.  

**41. What are NP-complete problems?**  
Problems that are in NP and as hard as any other NP problem.  

**42. What are NP-hard problems?**  
Problems at least as hard as NP-complete problems but not necessarily in NP.  

**43. Is TSP NP-complete or NP-hard?**  
TSP is **NP-hard**.  

**44. What is polynomial reduction?**  
Transforming one problem into another in polynomial time to prove complexity.  

---

### **Miscellaneous**  

**45-50. Additional algorithmic concepts**  
- Quick Sort is faster in practice due to **better cache performance**.  
- Huffman coding is **optimal** because it creates the shortest prefix-free codes.  
- The **halting problem** proves that some problems can't be solved algorithmically.  
