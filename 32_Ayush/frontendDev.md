# Technical Interview Questions & Answers
## Ayush Kumar
### B.Tech CSE | DSA | Python | React | Full Stack Development

---

# 1. Why is BFS guaranteed to find the shortest path in an unweighted graph while DFS is not?

### Answer
BFS explores nodes level by level. Therefore, the first time a node is reached, it is reached using the minimum number of edges.

DFS may travel deep into a longer path before discovering a shorter one.

Time Complexity: O(V + E)

---

# 2. Why can BFS become impractical for very large graphs?

### Answer
BFS stores every node at the current frontier in memory.

For a graph with millions of nodes, the queue can become extremely large and consume huge amounts of RAM.

---

# 3. Explain a scenario where HashMap complexity becomes O(n).

### Answer
HashMaps provide O(1) average lookup.

However, if many keys generate the same hash value, collisions occur.

In the worst case, all elements end up in one bucket, making lookup O(n).

---

# 4. Why is Merge Sort preferred over Quick Sort in some applications?

### Answer
Merge Sort guarantees O(n log n) in all cases.

Quick Sort has a worst-case complexity of O(n²).

Systems requiring predictable performance often choose Merge Sort.

---

# 5. Why must Binary Search be used only on sorted data?

### Answer
Binary Search eliminates half of the search space after every comparison.

Without sorting, there is no guarantee that the target lies in the left or right half.

---

# 6. What problem does Dynamic Programming solve?

### Answer
Dynamic Programming solves problems containing:

- Overlapping Subproblems
- Optimal Substructure

It avoids repeated calculations by storing previously computed results.

---

# 7. Why does Dijkstra's Algorithm fail for negative edge weights?

### Answer
Dijkstra assumes that once a node receives the shortest distance, it can never improve.

Negative edges can later produce a shorter path, violating this assumption.

Bellman-Ford should be used instead.

---

# 8. Explain Union Find and its applications.

### Answer
Union Find (Disjoint Set Union) efficiently manages connected components.

Applications:

- Kruskal's MST
- Cycle Detection
- Network Connectivity

Operations:

- Find()
- Union()

Complexity:
Nearly O(1)

---

# 9. Difference between Greedy and Dynamic Programming.

### Answer

Greedy:
- Makes locally optimal choices.
- Does not revisit decisions.

Dynamic Programming:
- Evaluates all possible subproblems.
- Guarantees optimal solution if applicable.

---

# 10. Explain Time Complexity and Space Complexity.

### Answer

Time Complexity:
Measures execution time growth.

Space Complexity:
Measures memory growth.

Example:

Binary Search:
Time → O(log n)
Space → O(1)

---

# Python

## 11. Why are Python dictionaries faster than lists for searching?

### Answer
Dictionaries use hash tables.

Dictionary Lookup:
O(1)

List Search:
O(n)

---

## 12. Difference between Deep Copy and Shallow Copy.

### Answer

Shallow Copy:
Copies references.

Deep Copy:
Creates completely independent copies.

---

## 13. Why are tuples hashable but lists are not?

### Answer

Tuples are immutable.

Lists are mutable.

Hashable objects must not change after creation.

---

## 14. What happens internally when:

```python
a = b
```

### Answer

No copy is created.

Both variables point to the same memory object.

---

## 15. Explain Python's GIL.

### Answer

GIL = Global Interpreter Lock

Only one thread executes Python bytecode at a time.

It simplifies memory management but limits CPU-bound multithreading.

---

## 16. Why use generators?

### Answer

Generators create values on demand.

Benefits:

- Lower memory usage
- Faster for large datasets

---

## 17. Difference between List Comprehension and Generator Expression.

### Answer

List Comprehension:

```python
[x*x for x in range(10)]
```

Creates the entire list.

Generator Expression:

```python
(x*x for x in range(10))
```

Generates values one by one.

---

## 18. Complexity of Set Lookup.

### Answer

Average Case:
O(1)

Worst Case:
O(n)

---

## 19. What are Decorators?

### Answer

Decorators modify function behavior without changing the original code.

Example:

```python
@login_required
def dashboard():
```

---

## 20. Why are mutable default arguments dangerous?

### Answer

```python
def func(arr=[]):
```

The list is created once and reused across function calls.

This can create unexpected bugs.

---

# DBMS

## 21. Explain ACID Properties.

### Answer

Atomicity:
All or nothing.

Consistency:
Database remains valid.

Isolation:
Transactions do not interfere.

Durability:
Changes survive crashes.

---

## 22. What happens if two users bid simultaneously in BidHub?

### Answer

Race conditions may occur.

Solutions:

- Transactions
- Row Locking
- Optimistic Locking

---

## 23. Why can indexes slow down databases?

### Answer

Indexes speed up reading.

But every INSERT, UPDATE, DELETE must also update the index.

---

## 24. Difference between Clustered and Non-Clustered Index.

### Answer

Clustered:
Physically sorts data.

Non-Clustered:
Separate structure referencing data.

---

## 25. What is a Deadlock?

### Answer

Two transactions wait indefinitely for each other to release resources.

---

# Operating Systems

## 26. Difference between Process and Thread.

### Answer

Process:
Independent execution unit.

Thread:
Lightweight execution unit inside a process.

---

## 27. What is Context Switching?

### Answer

CPU switches execution from one process/thread to another.

---

## 28. Why are threads faster than processes?

### Answer

Threads share memory.

Processes require separate memory spaces.

---

## 29. Explain Virtual Memory.

### Answer

Virtual Memory allows programs to use more memory than physically available using disk storage.

---

## 30. Explain Deadlock Conditions.

### Answer

1. Mutual Exclusion
2. Hold and Wait
3. No Preemption
4. Circular Wait

All four must exist simultaneously.

---

# Networking

## 31. What happens when you type google.com in a browser?

### Answer

1. DNS Lookup
2. TCP Handshake
3. HTTPS Connection
4. Request Sent
5. Response Received
6. Browser Rendering

---

## 32. Explain Three-Way Handshake.

### Answer

Client → SYN

Server → SYN-ACK

Client → ACK

Connection Established.

---

## 33. Why is TCP reliable?

### Answer

- Acknowledgements
- Retransmissions
- Sequence Numbers

---

## 34. Difference between TCP and UDP.

### Answer

TCP:
Reliable

UDP:
Faster but unreliable

---

## 35. Explain DNS.

### Answer

DNS converts domain names into IP addresses.

---

# React

## 36. What is Virtual DOM?

### Answer

A lightweight copy of the real DOM.

React updates only changed elements.

---

## 37. Why are keys required in React lists?

### Answer

Keys help React identify changed elements efficiently.

---

## 38. What is Reconciliation?

### Answer

Process React uses to compare old and new Virtual DOM trees.

---

## 39. Difference between State and Props.

### Answer

State:
Managed inside component.

Props:
Passed from parent component.

---

## 40. What causes unnecessary re-renders?

### Answer

- State changes
- Parent re-renders
- New object references

---

# BidHub Project

## 41. How would you scale BidHub for 1 million users?

### Answer

- Load Balancer
- Database Replication
- Redis Caching
- CDN
- Microservices

---

## 42. Why use WebSockets for bidding?

### Answer

WebSockets provide real-time bid updates without repeated polling.

---

## 43. How would you prevent race conditions in bidding?

### Answer

Database transactions and row-level locking.

---

## 44. What is the hardest problem in auction systems?

### Answer

Maintaining bid consistency during concurrent updates.

---

## 45. How would you synchronize auction timers?

### Answer

Server-side timer.

Never trust client clocks.

---

# Advanced Questions

## 46. Explain CAP Theorem.

### Answer

Distributed systems can guarantee only two:

- Consistency
- Availability
- Partition Tolerance

---

## 47. Difference between Horizontal and Vertical Scaling.

### Answer

Vertical:
Increase server power.

Horizontal:
Add more servers.

---

## 48. What is Load Balancing?

### Answer

Distributing traffic among multiple servers.

---

## 49. What is Caching?

### Answer

Storing frequently accessed data for faster retrieval.

---

## 50. Explain REST API principles.

### Answer

- Stateless
- Client-Server
- Uniform Interface
- Cacheable

---

(Continue similarly until Question 70)