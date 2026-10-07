# Graph Traversal: Eulerian and Hamiltonian Graphs

---

## 1. Introduction

Graphs are one of the most useful structures in **Discrete Mathematics and Computer Science**. They allow us to represent relationships and connections between different objects.

A graph consists mainly of:

* **Vertices (V):** Points or nodes
* **Edges (E):** Connections between vertices

For example:

```text
       A
      / \
     /   \
    B-----C
```

Here:

* `A, B, C` are vertices.
* `AB, BC, CA` are edges.

Graph traversal is the process of moving through a graph according to a particular rule.

Two important types of graph traversal are:

### Eulerian Traversal

Focuses on **edges**.

### Hamiltonian Traversal

Focuses on **vertices**.

> **Easy rule to remember:**
> **Euler → Edges**
> **Hamiltonian → Vertices**

---

# 2. Understanding Paths and Cycles

Before studying Eulerian and Hamiltonian graphs, we need to understand two basic terms.

### Path

A **path** is a sequence of vertices connected by edges.

Example:

```text
A → B → C → D
```

### Cycle

A **cycle** is a path that starts and ends at the same vertex.

```text
A → B → C → D → A
```

The starting and ending vertex are the same.

---

# 3. Eulerian Graphs

## What is an Eulerian Graph?

A connected graph is called **Eulerian** if it contains an **Eulerian circuit**.

An Eulerian circuit:

* Starts at a vertex.
* Travels through **every edge exactly once**.
* Returns to the starting vertex.

### Example

```text
       A
      / \
     /   \
    B-----C
```

One possible traversal is:

```text
A → B → C → A
```

Every edge is used exactly once, and the traversal returns to `A`.

Therefore, this graph has an **Eulerian circuit**.

---

# 4. Euler Path vs Euler Circuit

These two terms are closely related.

| Type              | Meaning                                                         |
| ----------------- | --------------------------------------------------------------- |
| **Euler Path**    | Uses every edge exactly once                                    |
| **Euler Circuit** | Uses every edge exactly once and returns to the starting vertex |

### Euler Path

```text
A ─── B ─── C
```

Traversal:

```text
A → B → C
```

It starts at `A` and ends at `C`.

### Euler Circuit

```text
      A
     / \
    B---C
```

Traversal:

```text
A → B → C → A
```

It returns to the starting vertex.

---

# 5. How to Identify an Eulerian Graph?

For a **connected undirected graph**, the degrees of the vertices provide a simple test.

### Eulerian Circuit

If **every vertex has an even degree**, the graph has an Eulerian circuit.

```text
All vertices have even degree
            ↓
    Eulerian Circuit
```

### Euler Path

If **exactly two vertices have odd degree**, the graph has an Euler path but not an Eulerian circuit.

```text
Exactly 2 odd-degree vertices
            ↓
        Euler Path
```

### No Euler Path

If there are **more than two odd-degree vertices**, there is no Euler path.

### Quick Reference

| Odd-Degree Vertices | Result           |
| ------------------: | ---------------- |
|                   0 | Eulerian circuit |
|                   2 | Euler path       |
|         More than 2 | No Euler path    |

---

# 6. Example: Eulerian Graph

Consider:

```text
      A
     / \
    B---C
```

The degree of each vertex is:

```text
Degree(A) = 2
Degree(B) = 2
Degree(C) = 2
```

All degrees are even.

Therefore:

**Eulerian circuit exists.**

Possible circuit:

```text
A → B → C → A
```

---

# 7. Hamiltonian Graphs

## What is a Hamiltonian Graph?

A graph is called **Hamiltonian** if it contains a **Hamiltonian cycle**.

A Hamiltonian cycle:

* Visits every vertex exactly once.
* Returns to the starting vertex.

The important point is that Hamiltonian graphs focus on **vertices**, not edges.

### Example

```text
       A
      / \
     /   \
    B     D
     \   /
      \ /
       C
```

A Hamiltonian cycle can be:

```text
A → B → C → D → A
```

Every vertex is visited exactly once.

Therefore, the graph contains a Hamiltonian cycle.

---

# 8. Hamiltonian Path vs Hamiltonian Cycle

| Type                  | Meaning                                                   |
| --------------------- | --------------------------------------------------------- |
| **Hamiltonian Path**  | Visits every vertex exactly once                          |
| **Hamiltonian Cycle** | Visits every vertex exactly once and returns to the start |

### Hamiltonian Path

```text
A ─── B ─── C ─── D
```

Traversal:

```text
A → B → C → D
```

Every vertex is visited once.

### Hamiltonian Cycle

```text
      A
     / \
    B   D
     \ /
      C
```

Traversal:

```text
A → B → C → D → A
```

Every vertex is visited once before returning to `A`.

---

# 9. Eulerian vs Hamiltonian

This is the most important comparison in this topic.

| Feature                       | Eulerian                   | Hamiltonian                     |
| ----------------------------- | -------------------------- | ------------------------------- |
| Main focus                    | **Edges**                  | **Vertices**                    |
| Path                          | Euler path                 | Hamiltonian path                |
| Cycle                         | Eulerian circuit           | Hamiltonian cycle               |
| What is visited exactly once? | Every edge                 | Every vertex                    |
| Can vertices repeat?          | Yes, in an Euler traversal | No, except start/end of a cycle |
| Simple general test           | Based on vertex degrees    | No simple equivalent test       |
| Typical problem               | Cover every road           | Visit every city                |

### Memory Trick

```text
┌─────────────────────────┐
│        EULERIAN         │
│           ↓             │
│     Every EDGE          │
└─────────────────────────┘

┌─────────────────────────┐
│       HAMILTONIAN       │
│           ↓             │
│    Every VERTEX         │
└─────────────────────────┘
```

---

# 10. A Graph Can Be Both

An important point is that a graph can be **both Eulerian and Hamiltonian**.

Consider a simple cycle:

```text
      A
     / \
    B   D
     \ /
      C
```

Eulerian traversal:

```text
A → B → C → D → A
```

Every edge is used exactly once.

Hamiltonian traversal:

```text
A → B → C → D → A
```

Every vertex is visited exactly once.

Therefore, the graph is:

**Eulerian + Hamiltonian**

---

# 11. Eulerian Does Not Mean Hamiltonian

Being Eulerian does **not** automatically make a graph Hamiltonian.

The two concepts have different requirements.

```text
Eulerian
   ↓
Every edge exactly once

Hamiltonian
   ↓
Every vertex exactly once
```

A graph may satisfy one condition without satisfying the other.

Therefore, they should always be checked separately.

---

# 12. Hamiltonian Does Not Mean Eulerian

Similarly, a graph can be Hamiltonian without being Eulerian.

A graph may contain a cycle that visits every vertex exactly once, while some vertices have odd degree.

In that case:

```text
Hamiltonian ✓
Eulerian    ✗
```

This demonstrates why the two concepts should not be confused.

---

# 13. Important Theorem: Euler's Theorem

For a connected undirected graph:

> A graph has an Eulerian circuit if and only if every vertex has even degree.

For example:

```text
Degree(A) = 2
Degree(B) = 2
Degree(C) = 4
Degree(D) = 2
```

Since every degree is even:

```text
Eulerian Circuit ✓
```

This makes Eulerian graphs relatively easy to identify.

---

# 14. Hamiltonian Graphs and Dirac's Theorem

Hamiltonian graphs are generally more difficult to identify.

One important result is **Dirac's Theorem**.

For a simple graph with `n ≥ 3` vertices, if every vertex has degree at least:

$$
\frac{n}{2}
$$

then the graph contains a Hamiltonian cycle.

In simple terms:

> If every vertex is connected to at least half of the other vertices, a Hamiltonian cycle is guaranteed.

This is a **sufficient condition**, not a necessary one.

---

# 15. Real-World Applications

Graph traversal is not just a mathematical concept. It is useful in many real-world problems.

## Eulerian Applications

Eulerian concepts are useful when we need to cover **connections or routes**.

### Road Inspection

A worker may need to travel along every road in an area.

```text
Roads → Edges
```

The problem can be modeled using Eulerian concepts.

### Garbage Collection

A garbage collection vehicle may need to cover a set of roads efficiently.

### Network Testing

A network engineer may want to test every communication link.

### Postal Delivery

A postal route may require covering many streets or connections.

---

# 16. Hamiltonian Applications

Hamiltonian concepts are useful when we need to visit **locations or objects**.

### Travelling Salesperson Problem

A salesperson needs to:

1. Visit every city.
2. Visit each city once.
3. Return to the starting city.

This can be represented using a Hamiltonian cycle.

```text
       City A
      /      \
   City B   City D
      \      /
       City C
```

Possible route:

```text
A → B → C → D → A
```

### Other Applications

Hamiltonian concepts can also appear in:

* Delivery planning
* Scheduling
* Circuit design
* Network planning
* Route optimization

---

# 17. Eulerian vs Hamiltonian: Real-Life Example

Imagine a delivery company.

### Problem 1: Cover Every Road

The driver must travel through every required road.

```text
Roads = Edges
```

This is an **Eulerian-type problem**.

### Problem 2: Visit Every Customer

The driver must visit every customer exactly once and return to the warehouse.

```text
Customers = Vertices
```

This is a **Hamiltonian-type problem**.

### Easy Way to Think About It

```text
"Have I covered every CONNECTION?"
             ↓
          EULERIAN

"Have I visited every LOCATION?"
             ↓
        HAMILTONIAN
```

---

# 18. Eulerian and Hamiltonian Traversal at a Glance

```text
                    GRAPH
                      │
          ┌───────────┴───────────┐
          │                       │
      EULERIAN                HAMILTONIAN
          │                       │
     Focus on edges          Focus on vertices
          │                       │
   Every edge once          Every vertex once
          │                       │
   Euler Path/Circuit       Hamiltonian Path/Cycle
```

---

# 19. Common Mistakes

### Mistake 1: Confusing edges and vertices

Incorrect:

> Eulerian graphs visit every vertex once.

Correct:

> Eulerian graphs focus on visiting every edge exactly once.

---

### Mistake 2: Thinking every Hamiltonian graph is Eulerian

This is false.

A Hamiltonian graph may contain vertices with odd degrees.

---

### Mistake 3: Assuming an Euler path must return to the start

It does not.

Only an **Eulerian circuit** must return to the starting vertex.

---

### Mistake 4: Assuming Hamiltonian traversal can repeat vertices

A Hamiltonian path or cycle visits each vertex exactly once, except that the starting vertex appears again at the end of a Hamiltonian cycle.

---

# 20. Quick Problem-Solving Guide

When you are given a graph in an examination, ask:

### For Eulerian

**Question:**

> Can I use every edge exactly once?

Then check vertex degrees.

```text
0 odd degrees → Eulerian circuit
2 odd degrees → Euler path
More than 2 → No Euler path
```

### For Hamiltonian

**Question:**

> Can I visit every vertex exactly once?

Try to construct a path or cycle containing every vertex.

---

# 21. Quick Revision Sheet

| Term              | Definition                                    |
| ----------------- | --------------------------------------------- |
| Graph             | Set of vertices and edges                     |
| Vertex            | A node in a graph                             |
| Edge              | Connection between vertices                   |
| Path              | Sequence of connected vertices                |
| Cycle             | Closed path                                   |
| Euler Path        | Uses every edge exactly once                  |
| Eulerian Circuit  | Uses every edge once and returns to start     |
| Hamiltonian Path  | Visits every vertex exactly once              |
| Hamiltonian Cycle | Visits every vertex once and returns to start |

---

# 22. The One-Minute Summary

If you remember only four things from this article, remember these:

### 1. Eulerian = Edges

```text
Every EDGE exactly once
```

### 2. Hamiltonian = Vertices

```text
Every VERTEX exactly once
```

### 3. Eulerian Circuit

```text
All vertices have even degree
```

### 4. Hamiltonian Cycle

```text
Every vertex is visited once
and we return to the starting vertex.
```

---

# 23. Conclusion

Eulerian and Hamiltonian graphs are fundamental concepts in graph theory and Discrete Structures.

Although both involve paths and cycles, their goals are different.

**Eulerian graphs focus on edges**, making them useful for problems such as road inspection, network testing, and route coverage.

**Hamiltonian graphs focus on vertices**, making them useful for problems such as city tours, delivery planning, and route optimization.

The simplest way to remember the difference is:

> **Euler → Every Edge**
> **Hamiltonian → Every Vertex**

Understanding this distinction provides a strong foundation for studying graph algorithms, optimization, and more advanced topics in computer science.

---

## Key Takeaway

```text
                 GRAPH TRAVERSAL
                       │
            ┌──────────┴──────────┐
            │                     │
         EULERIAN             HAMILTONIAN
            │                     │
       Focus: EDGES          Focus: VERTICES
            │                     │
    Every edge once          Every vertex once
            │                     │
    Euler Path/Circuit      Hamiltonian Path/Cycle
```

**In short:**

> **Eulerian → Cover the connections.**
> **Hamiltonian → Visit the locations.**

