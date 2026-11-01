# 🧩 Data Structures & Algorithms (DSA)

This section contains solutions, patterns, and problem-solving strategies implemented in Java with an emphasis on production-grade code, optimal time/space complexities, and clean explanations.

---

## 📑 Core Resource

👉 **[NeetCode 150 - Full Java Solutions & Explanations](./neetcode150.md)**
- Complete collection of 150 high-frequency interview problems covering all 18 topics.
- Every solution includes:
  - Problem statement & constraints
  - Intuition & approach
  - Runnable Java code with sample test cases in `main`
  - Big-O Time and Space complexity breakdown

---

## 🧭 Essential Problem-Solving Patterns

| # | Pattern | When to Use | Classic Problems |
|---|---|---|---|
| 1 | **Two Pointers** | Sorted arrays, palindrome verification, searching pairs | Valid Palindrome, 3Sum, Container With Most Water |
| 2 | **Sliding Window** | Subarrays/substrings matching a condition (fixed or dynamic window) | Best Time to Buy/Sell Stock, Longest Substring Without Repeating Characters |
| 3 | **Fast & Slow Pointers** | Cycle detection, finding middle of linked lists | Linked List Cycle, Find the Duplicate Number |
| 4 | **Monotonic Stack / Queue** | Next greater/smaller element, histograms | Daily Temperatures, Largest Rectangle in Histogram |
| 5 | **Binary Search (Variants)** | Sorted space, finding min/max condition (search on answer) | Search in Rotated Sorted Array, Koko Eating Bananas |
| 6 | **Backtracking** | Permutations, combinations, subsets, constraint satisfaction | Subsets, Combination Sum, N-Queens, Word Search |
| 7 | **BFS & DFS (Trees / Graphs)** | Level-order traversal, shortest path in unweighted graphs, connected components | Clone Graph, Course Schedule, Rotting Oranges |
| 8 | **Topological Sort** | Dependency resolution, task scheduling | Course Schedule II, Alien Dictionary |
| 9 | **Disjoint Set Union (Union-Find)** | Dynamic connectivity, cycle detection in undirected graphs | Number of Connected Components, Redundant Connection |
| 10 | **Dynamic Programming (1D & 2D)** | Overlapping subproblems and optimal substructure | Coin Change, Longest Common Subsequence, Edit Distance |

---

## ⚡ Big-O Complexity Quick Reference

### Data Structure Operations

| Data Structure | Access | Search | Insertion | Deletion | Space |
|---|---|---|---|---|---|
| **Array / ArrayList** | $O(1)$ | $O(n)$ | $O(1)$ amortized (end) / $O(n)$ (arbitrary) | $O(n)$ | $O(n)$ |
| **LinkedList** | $O(n)$ | $O(n)$ | $O(1)$ (with pointer) | $O(1)$ (with pointer) | $O(n)$ |
| **Stack / Queue** | $O(n)$ | $O(n)$ | $O(1)$ | $O(1)$ | $O(n)$ |
| **HashSet / HashMap** | $N/A$ | $O(1)$ avg / $O(n)$ worst | $O(1)$ avg / $O(n)$ worst | $O(1)$ avg / $O(n)$ worst | $O(n)$ |
| **TreeSet / TreeMap** | $N/A$ | $O(\log n)$ | $O(\log n)$ | $O(\log n)$ | $O(n)$ |
| **Binary Heap (PriorityQueue)** | $O(1)$ (peek min/max) | $O(n)$ | $O(\log n)$ | $O(\log n)$ | $O(n)$ |
| **Trie (Prefix Tree)** | $N/A$ | $O(L)$ where $L$ is word length | $O(L)$ | $O(L)$ | $O(\Sigma \cdot L)$ |

---

## 🎯 Recommended Practice Strategy

1. **Topic-by-Topic:** Start with *Arrays & Hashing*, then *Two Pointers*, *Sliding Window*, *Stack*, and *Binary Search* before moving to trees and graphs.
2. **Implement From Scratch:** Avoid memorizing syntax; practice writing edge cases, boundary checks, and dry-running on sample inputs.
3. **Analyze Complexity First:** Always state the time and space complexity before writing code.

