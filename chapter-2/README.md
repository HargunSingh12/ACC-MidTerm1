# Chapter 2: Linear Data Structures

COMP 8547 Advanced Computing Concepts, Mid-Term I (Friday 23 October 2026). This page covers **only Chapter 2**: maps, hash tables, priority queues and heaps. Everything comes from the Chapter 2 slides. Practice questions for this chapter are in [questions.md](questions.md).

**On this page**
1. [Abstract data types](#1-abstract-data-types)
2. [The Map ADT](#2-the-map-adt)
3. [Hash tables](#3-hash-tables)
4. [Collision handling](#4-collision-handling)
5. [Load factor, performance and rehashing](#5-load-factor-performance-and-rehashing)
6. [Hash tables in Java](#6-hash-tables-in-java)
7. [Advanced hashing](#7-advanced-hashing)
8. [Priority queues](#8-priority-queues)
9. [Tree terminology](#9-tree-terminology)
10. [Binary heaps](#10-binary-heaps)
11. [Heap construction](#11-heap-construction)
12. [Other heaps](#12-other-heaps)
13. [Heaps in Java](#13-heaps-in-java)
14. [Applications](#14-applications)
15. [Last-minute checklist](#15-last-minute-checklist)

---

## 1. Abstract data types

> An **abstract data type (ADT)** is a set of objects together with a set of operations.

- It is a mathematical abstraction.
- Its definition covers the **data**, the **operations** and the **error conditions**.
- An implementation adds algorithms, with their time and space complexities.
- Examples: lists, stacks, array lists, sets, maps, dictionaries, heaps, hash tables, graphs.
- Typical operations: add, remove, contains, union, find, min, insert, delete.

## 2. The Map ADT

A **map** is a searchable collection of **key-value entries**. Its main operations are searching, inserting and deleting. Assume the keys are unique.

| Method | What it does |
|---|---|
| `size()`, `isEmpty()` | number of entries / whether there are none |
| `get(k)` | the value for key k, or **null** |
| `put(k, v)` | inserts (k, v). Returns **null** if k was new, otherwise the **old value** |
| `remove(k)` | removes the entry and returns its value, or **null** |
| `keys()`, `values()` | iterators over the keys / values |

Applications: address books, student-record databases, word counts.

Implementations:
- **Sorted maps:** array list with binary search, skip list, binary search tree.
- **Unsorted maps:** hash table.

## 3. Hash tables

A hash table has two parts:
- a **hash function h** that maps keys to integers in **[0, N − 1]**, for example **h(x) = x mod N**
- a **bucket array** (the table) of size N

The goal is to store the entry (k, o) at index **i = h(k)**. h(x) is called the **hash value** of x.
Slide example: SINs in an array of size N = 1,000, indexed by the last three digits.

A **collision** happens when two keys map to the same cell.

## 4. Collision handling

### Separate chaining
Each cell points to a **linked list** of the entries that hash there. Simple, but it needs extra memory.

### Open addressing
The colliding item goes into **another cell of the table**. There are three main techniques.

| Technique | Cells tried for j = 1, 2, … | Problem |
|---|---|---|
| **Linear probing** | (i + j) mod N | **primary clustering**: colliding items lump together, so later collisions need longer probe sequences |
| **Quadratic probing** | (i + j²) mod N | avoids primary clustering but causes **secondary clustering** (filled cells bounce around in a fixed pattern). **Not guaranteed to find an empty cell** |
| **Double hashing** | (i + j·d2(k)) mod N | needs a second hash d2(k) that is **never 0** and a **prime** N |

**Linear probing removals:** a removed cell is marked **"A"** (available). Searches **continue past it**, and insertions can reuse it.

**Double hashing rules:**
- usual secondary hash: **d2(k) = q − (k mod q)**
- q < N, and **q and N are both prime**
- d2(k) takes values 1, 2, …, q, so never 0
- a prime N lets the probe sequence reach every cell

### Slide examples (N = 13, h(k) = k mod 13)

**Linear probing**, inserting 18, 41, 22, 44, 59, 32, 31, 73:

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| | | 41 | | | 18 | 44 | 59 | 32 | 22 | 31 | 73 | |

Removing 31 puts "A" in cell 10.

**Quadratic probing**, inserting 18, 41, 31, 54, 28, 44, 15:

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| | 15 | 41 | 54 | | 18 | 31 | | | 44 | | 28 | |

**Double hashing** with d2(k) = 7 − (k mod 7), inserting 18, 41, 22, 44, 59, 32, 31, 73:

| k | h(k) | d2(k) | probes |
|---|---|---|---|
| 18 | 5 | 3 | 5 |
| 41 | 2 | 1 | 2 |
| 22 | 9 | 6 | 9 |
| 44 | 5 | 5 | 5, 10 |
| 59 | 7 | 4 | 7 |
| 32 | 6 | 3 | 6 |
| 31 | 5 | 4 | 5, 9, 0 |
| 73 | 8 | 4 | 8 |

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 31 | | 41 | | | 18 | 32 | 59 | 73 | 22 | 44 | | |

## 5. Load factor, performance and rehashing

- **Load factor α = n/N** (entries / table size).
- Expected probes for a search with linear probing: **p = ½ (1 + 1/(1 − α))**
  - as α → 0, p is a constant
  - as α → 1, p → ∞
- **Ideal load factor < 0.5.** Then search, insertion and removal are **expected O(1)**.
- Worst case for a search is **O(n)**, when everything collides.

**Rehashing** is the fix when the table is full or α is too high:
1. Create a new, larger, empty table (slide example: h(x) = x mod 13 becomes x mod 23).
2. Remove every element from the old table, one at a time.
3. Insert each one into the new table.

## 6. Hash tables in Java

- `HashMap` implements a hash table using **separate chaining**.
- Default **capacity 16**, default **load factor 0.75**.
- Constructor: `HashMap(int initialCapacity, float loadFactor)`.
- It implements the `Map` interface, with generic key and value types.

## 7. Advanced hashing

| Scheme | Main idea |
|---|---|
| **Cuckoo hashing** | Two tables. Insert into Table 1; if the cell holds k′, **displace** k′ into Table 2; if that cell holds k″, move k″ back to Table 1, and so on until an empty cell is found. With a low load factor more than O(log N) displacements is unlikely. After too many displacements, **rebuild** the table |
| **Perfect hashing** | Separate chaining where each list holds at most a constant number of keys, so a search is **worst-case O(1)** |
| **Hopscotch hashing** | Based on linear probing; after a collision the item is placed **no more than max_dist** from its initial probe. Newer, still experimental |
| **Universal hashing** | The hash function is computed in constant time, so insertions and searches are O(1) |
| **Extendible hashing** | For **large datasets on disk**. Stores entries in disk blocks of M records, uses a **directory** to reach the blocks, and aims for searches in **at most two disk accesses**. Insertions may need a few disk accesses |

## 8. Priority queues

A **priority queue (PQ)** stores entries (key, value).

Main methods:
- `insert(k, x)`: insert an entry with key k and value x
- `insertLast(k)`: insert at the end
- `removeMin()`: remove and return the entry with the smallest key
- `min()`: return, without removing, an entry with the smallest key

Keys are compared with a **Comparator**. `compare(a, b)` returns **< 0** if a < b, **0** if a = b, **> 0** if a > b, and raises an error if a and b cannot be compared. The comparison defines a total order.

| Implementation | min / removeMin | insert |
|---|---|---|
| Sorted list | **O(1)** | O(n) |
| Unsorted list in any order | O(n) | O(1) |
| **Heap** | removeMin **O(log n)** (min itself is O(1)) | **O(log n)** |

Applications: Huffman coding trees, search techniques, operating systems (scheduling), sorting and selection.

## 9. Tree terminology

A tree is an undirected acyclic graph. This chapter uses **rooted** trees: a set of nodes with a parent-child relation. A non-empty tree has one root, and every other node has exactly one parent. A tree can be empty.

- **Root:** the node without a parent.
- **Internal node:** has at least one child.
- **External node (leaf):** has no children.
- **Ancestors:** parent, grandparent, and so on. **Descendants:** child, grandchild, and so on.
- **Depth of a node:** its number of ancestors.
- **Height of a tree:** the maximum depth of any node.
- **Subtree:** a node and all its descendants.

**Binary tree:** each internal node has at most two children (exactly two in a **proper** binary tree), forming an ordered pair (left child, right child). Recursive definition: a binary tree is empty, a single node, or a root whose two children are both binary trees.

## 10. Binary heaps

A **heap** is a binary tree that stores keys at its nodes and satisfies two properties:
1. **Heap order:** for every node v other than the root, **key(v) ≥ key(parent(v))**. So the minimum is at the root.
2. **Complete binary tree:** with height h, depths 0 … h − 1 are full (2ⁱ nodes at depth i), and at depth h the nodes fill **from the left**.

The **last node** is the rightmost node at depth h.

**Theorem: a heap with n keys has height O(log n).**
Proof: n ≥ 1 + 2 + 4 + … + 2ʰ⁻¹ + 1 = 2ʰ, so h ≤ log n.

### Insertion: O(log n)
1. Find the insertion node z, the new last node.
2. Store k at z.
3. **Upheap:** swap k with its parent while the parent's key is larger. Stop at the root or at a parent with key ≤ k.

### removeMin: O(log n)
1. Replace the root's key with the key of the last node w.
2. Remove w.
3. **Downheap:** swap k with its **smaller** child while that child is smaller. Stop at a leaf or when both children are ≥ k.

### Array representation
- n keys go in an array of size **n + 1**; **index 0 is unused**.
- Node at rank i: **left child 2i**, **right child 2i + 1**, **parent ⌊i/2⌋**.
- No links are stored.
- `insert` writes at rank n + 1; `removeMin` takes rank 1.

Example: the heap 2 / 5 6 / 9 7 is stored as `[–, 2, 5, 6, 9, 7]`.

## 11. Heap construction

- Inserting n keys one by one costs **O(n log n)**.
- **Bottom-up construction costs O(n)**, using about log n phases. In phase i, pairs of heaps with 2ⁱ − 1 keys are merged into heaps with 2ⁱ⁺¹ − 1 keys.

```
Algorithm BottomUpHeap(S)          // S has n = 2^h − 1 keys
  if S is empty then return an empty heap
  k ← S[0]
  split S[1..n−1] into S1 and S2
  H1 ← BottomUpHeap(S1)
  H2 ← BottomUpHeap(S2)
  create H with k at the root, H1 as left child and H2 as right child
  Downheap(H, root)
  return H
```

**Array version** (same idea): for i from ⌊n/2⌋ down to 1, downheap(i).

### d-heaps
- A generalisation of the binary heap: each node has up to d children.
- Shallower: height **O(log_d n)**.
- Insert and removeMin are still **O(log n)**, since log_d n = log₂ n / log₂ d and log₂ d is a constant.
- Experiments suggest a **4-heap may outperform** the binary heap.

## 12. Other heaps

| Heap | Key facts |
|---|---|
| **Leftist heap** | Same structural and ordering properties as binary heaps, but **not necessarily balanced** |
| **Skew heap** | Self-adjusting version of the leftist heap. Operations can take **O(n) worst case** but **O(log n) amortized** |
| **Binomial queue** | Not a heap in the strict sense: a **collection (forest) of heaps** |
| **Fibonacci heap** | Also a collection of heaps. removeMin and remove are **O(log n) amortized**; other operations are **O(1) amortized** |

## 13. Heaps in Java

- `java.util.PriorityQueue` implements a heap (a min-heap).
- You can pass a comparator: `PriorityQueue(int initialCapacity, Comparator<? super E> comparator)`.
- Insert with **`add(E e)`**; remove the minimum with **`poll()`**.

## 14. Applications

### Application 1: the selection problem
Find the k-th smallest key (or the k smallest keys) of an unsorted list of n keys.

| Approach | Steps | Time |
|---|---|---|
| Naive | sort with mergesort or heapsort, then pick the k-th | **O(n log n)** |
| Heap-based | build a heap bottom-up in O(n), then k × removeMin at O(log n) each | **O(n + k log n)** |

When k is much smaller than n, or constant, the heap approach is much better.

### Application 2: counting word frequencies
For every word in the documents:
- look it up in a hash table keyed by word
- if it is not found, insert it with frequency 1
- if it is found, add 1

Related problems: find the k most frequent words (use a heap), rank documents by frequent words, find documents by keywords.

### Other real-world uses
- **Hash tables:** caches, compiler symbol tables, database indexes, spell checkers, sets.
- **Heaps / priority queues:** OS job scheduling, Huffman coding, Dijkstra's shortest paths, event simulation, top-k queries.

## 15. Last-minute checklist

- [ ] Map methods and what `put`, `get` and `remove` return
- [ ] Fill a table by hand with linear, quadratic and double hashing
- [ ] Primary clustering (linear) vs secondary clustering (quadratic); quadratic can fail
- [ ] Double hashing: d2 = q − k mod q, q < N, both prime, never 0
- [ ] α = n/N, keep it below 0.5; probes ½(1 + 1/(1 − α)); rehash when too high
- [ ] HashMap: chaining, capacity 16, load factor 0.75
- [ ] Cuckoo, perfect, hopscotch, universal and extendible hashing in one line each
- [ ] PQ costs for a sorted list, an unsorted list and a heap
- [ ] Heap order + complete tree; height O(log n)
- [ ] Upheap / downheap traces in array form (children 2i and 2i + 1, parent ⌊i/2⌋)
- [ ] Bottom-up construction O(n); d-heap height log_d n
- [ ] Leftist, skew, binomial and Fibonacci heaps
- [ ] Selection with a heap: O(n + k log n)
