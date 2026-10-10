# Chapter 2: Linear Data Structures, Question Bank

Every question type from the Mid-Term I format, for **Chapter 2 only** (maps, hashing, priority queues, heaps). The answer key is at the bottom. Notes for this chapter are in [README.md](README.md).

| Part | Exam section | Questions |
|---|---|---|
| A | MCQ Level I (simple) | A1–A18 |
| B | MCQ Level II (scenarios) | B1–B12 |
| C | Short answer Level I (fill in) | C1–C20 |
| D | Short answer Level II (hands-on) | D1–D20 |

Heap arrays use **index 1 as the root** (index 0 unused) unless stated.

---

## Part A. MCQ Level I

**A1.** An abstract data type is: (a) a Java interface only (b) a set of objects with a set of operations (c) a memory address (d) an algorithm

**A2.** In the Map ADT, `get(k)` for a key that is not in the map returns: (a) 0 (b) an exception (c) null (d) the last value

**A3.** In the Map ADT, `put(k, v)` for a key that is **already** in the map returns: (a) null (b) v (c) the old value of k (d) true

**A4.** A hash function maps keys to: (a) any integer (b) integers in [0, N − 1] (c) strings (d) sorted positions

**A5.** Separate chaining stores colliding entries: (a) in the next free cell (b) in a linked list at the cell (c) in a second table (d) on disk

**A6.** Which open-addressing method suffers from **primary clustering**? (a) linear probing (b) quadratic probing (c) double hashing (d) separate chaining

**A7.** Which method is **not guaranteed** to find an empty cell even when one exists? (a) linear probing (b) quadratic probing (c) separate chaining (d) double hashing with a prime N

**A8.** In double hashing, the secondary hash d2(k) must never be: (a) prime (b) odd (c) 0 (d) less than N

**A9.** The load factor α of a hash table is: (a) N/n (b) n/N (c) n − N (d) log n

**A10.** The ideal load factor for open addressing is: (a) below 0.5 (b) exactly 1 (c) above 0.9 (d) 2

**A11.** Java's HashMap default capacity and load factor are: (a) 10 and 0.5 (b) 16 and 0.75 (c) 32 and 1.0 (d) 16 and 0.5

**A12.** Which hashing scheme is designed for large datasets on disk with at most two disk accesses per search? (a) cuckoo (b) hopscotch (c) extendible (d) universal

**A13.** The heap-order property of a min-heap says, for every non-root node v: (a) key(v) ≤ key(parent) (b) key(v) ≥ key(parent) (c) key(v) = key(parent) (d) left < right

**A14.** The last node of a heap is: (a) the root (b) the rightmost node at the deepest level (c) the largest key (d) the leftmost leaf

**A15.** Upheap stops when the key reaches the root or: (a) a leaf (b) a parent with a smaller or equal key (c) the last node (d) depth 1

**A16.** In array form (root at index 1), the parent of the node at index i is at: (a) i − 1 (b) 2i (c) ⌊i/2⌋ (d) i + 1

**A17.** A skew heap is: (a) a forest of heaps (b) a self-adjusting leftist heap (c) a d-heap with d = 3 (d) always balanced

**A18.** In java.util.PriorityQueue, `add(e)` and `poll()` respectively: (a) insert and remove the minimum (b) insert and peek (c) remove and insert (d) sort and clear

---

## Part B. MCQ Level II (scenarios)

**B1.** A student-records system needs fast lookup by student number, and never needs the records in order. Choose: (a) sorted array (b) hash table (c) min-heap (d) linked list

**B2.** You need the records **in key order** and also lookups by key. Choose: (a) hash table (b) sorted map (array with binary search or a search tree) (c) unsorted list (d) heap

**B3.** A hash table uses linear probing and its load factor is now 0.85; lookups have slowed down. Best action? (a) keep inserting (b) rehash into a larger prime-sized table (c) switch to a stack (d) sort the bucket array

**B4.** Your keys collide a lot and you want colliding keys to follow **different** probe sequences. Choose: (a) linear probing (b) quadratic probing (c) double hashing (d) no collision handling

**B5.** You need guaranteed worst-case O(1) lookups for a fixed set of keys. Choose: (a) linear probing (b) perfect hashing (c) unsorted list (d) binary heap

**B6.** An OS scheduler always runs the job with the smallest priority number, and jobs arrive all the time. Choose: (a) sorted array (b) hash table (c) binary heap / priority queue (d) stack

**B7.** You must find the 10 smallest values among 10 million unsorted values. Most efficient? (a) sort everything first (b) build a heap bottom-up, then 10 removeMins (c) 10 linear scans (d) a hash table

**B8.** You have all n keys up front and want a heap as fast as possible. Choose: (a) n separate inserts (b) bottom-up construction (c) sort, then insert (d) insert into a hash table first

**B9.** A priority queue has many inserts and very few removeMin calls. Which simple list is better? (a) sorted list (b) unsorted list (c) either (d) neither works

**B10.** A priority queue has very few inserts but calls min() constantly. Which simple list is better? (a) sorted list (b) unsorted list (c) either (d) neither works

**B11.** You want to count how many times each word appears in a large set of emails. Choose: (a) hash table keyed by word (b) min-heap of words (c) sorted array with insertion (d) a stack

**B12.** A heap must support very many inserts and removeMins on huge data, and you want a shallower tree than a binary heap. Choose: (a) a 4-heap (d-heap) (b) a sorted list (c) a skew heap (d) a hash table

---

## Part C. Short answer Level I

C1. The three parts of an ADT definition are data, operations and ______.
C2. An unsorted map is usually implemented with a ______.
C3. h(x) = x mod N maps keys to the range ______.
C4. In linear probing, a removed entry is marked with ______.
C5. Expected probes for a search with linear probing: p = ______.
C6. As α → 1, the expected number of probes tends to ______.
C7. Expected time of search, insert and remove in a hash table with α < 0.5: ______.
C8. Common secondary hash for double hashing: d2(k) = ______.
C9. Java's HashMap handles collisions with ______.
C10. In cuckoo hashing with a low load factor, more than ______ displacements are unlikely.
C11. Cost of removeMin in a priority queue implemented with a sorted list: ______.
C12. Cost of min() in a priority queue implemented with an unsorted list: ______.
C13. Height of a heap with n keys: ______.
C14. Time for insert and for removeMin in a binary heap: ______.
C15. An array storing a heap of n keys has size ______.
C16. Time to build a heap bottom-up: ______.
C17. Height of a d-heap with n keys: ______.
C18. In a Fibonacci heap, removeMin takes ______ amortized; other operations take ______ amortized.
C19. Time to find the k smallest keys with a heap: ______.
C20. comparator.compare(a, b) returns a value ______ 0 when a < b.

---

## Part D. Short answer Level II (hands-on)

**D1.** N = 7, h(k) = k mod 7, **linear probing**. Insert 10, 17, 24, 3, 31. Show the table.

**D2.** (Slide example) N = 13, h(k) = k mod 13, **quadratic probing**. Insert 18, 41, 31, 54, 28, 44, 15. Show the table.

**D3.** (Slide example) N = 13, h(k) = k mod 13, **double hashing** with d2(k) = 7 − (k mod 7). Insert 18, 41, 22, 44, 59, 32, 31, 73. Give h, d2 and the probes for each key and the final table.

**D4.** N = 5, h(k) = k mod 5, **separate chaining**. Insert 12, 7, 22, 5, 17, 3. Show the chains. What is the load factor?

**D5.** N = 10, h(k) = k mod 10, linear probing. Insert 42, 12, 22, 9, 19. (a) Show the table. (b) Remove 12. How many cells are probed when searching for 22? (c) Then insert 32. Where does it go?

**D6.** N = 7, h(k) = k mod 7, **quadratic probing**. Insert 0, 7, 14, 21, then try 28. What happens and why?

**D7.** Rehash the D1 table into N = 11 with h(k) = k mod 11 (linear probing, keys in the order 10, 17, 24, 3, 31). Give the new positions and the load factors before and after.

**D8.** Cuckoo hashing with two tables of size 7: h1(k) = k mod 7, h2(k) = ⌊k/7⌋ mod 7. Insert 15, 22, 8, 29 (always try Table 1 first). Show each displacement and both final tables.

**D9.** Compute the expected number of probes for a search with linear probing at α = 0.5, 0.75 and 0.9.

**D10.** Insert 10, 4, 15, 2, 8, 1, 6 into an empty min-heap. Give the array after all inserts, then after each of two removeMins.

**D11.** The heap `[2, 5, 6, 9, 7]` (index 1 onward). (a) Insert 3 and give the array. (b) Starting again from the original, do removeMin and give the array.

**D12.** Is each array a min-heap? Give a reason. (a) [2, 5, 6, 9, 7] (b) [3, 5, 4, 6, 2] (c) [1, 3, 2, 7, 4, 5, 6]

**D13.** Build a heap bottom-up (array version: downheap from i = ⌊n/2⌋ down to 1) from [16, 15, 4, 12, 6, 7, 23, 20]. Give the final array.

**D14.** Build a heap bottom-up (array version) from [9, 7, 5, 3, 1, 8, 6].

**D15.** In a heap stored from index 1: what are the children and the parent of the node at index 5? What is the height of a heap with 1,000 keys?

**D16.** In a 4-heap stored from **index 0**, give the children of the node at index i and its parent. What is the height of a 4-heap with 100 keys?

**D17.** Fill in the time of each operation:

| PQ implementation | insert | min | removeMin |
|---|---|---|---|
| Sorted list | | | |
| Unsorted list | | | |
| Heap | | | |

**D18.** Selection with n = 1,000,000 and k = 20. Compare the naive approach and the heap-based approach in Big-O.

**D19.** Using a hash table, count the word frequencies of "to be or not to be that is the question to ask". List the final (word, count) entries with count > 1.

**D20.** Explain why bottom-up heap construction is O(n) while n inserts are O(n log n). A valid justification is enough.

---
---

# Answer key

## Part A
A1 b · A2 c · A3 c · A4 b · A5 b · A6 a · A7 b · A8 c · A9 b · A10 a · A11 b · A12 c · A13 b · A14 b · A15 b · A16 c · A17 b · A18 a

## Part B
- B1 **b**: expected O(1) lookup, and order is not needed.
- B2 **b**: a hash table is unordered; a sorted map keeps keys in order.
- B3 **b**: rehashing lowers α back under 0.5.
- B4 **c**: double hashing gives each key its own step size d2(k), avoiding both kinds of clustering.
- B5 **b**: perfect hashing gives worst-case O(1).
- B6 **c**: insert and removeMin in O(log n).
- B7 **b**: O(n + k log n) with k = 10.
- B8 **b**: bottom-up is O(n); n inserts are O(n log n).
- B9 **b**: an unsorted list inserts in O(1), and the rare removeMin costs O(n).
- B10 **a**: a sorted list has the min at the front, O(1).
- B11 **a**: the slides' word-frequency application.
- B12 **a**: a d-heap has height O(log_d n); a 4-heap may beat a binary heap.

## Part C
C1 error conditions · C2 hash table · C3 [0, N − 1] · C4 "A" (available) · C5 ½(1 + 1/(1 − α)) · C6 infinity · C7 O(1) expected · C8 q − (k mod q), q < N, both prime · C9 separate chaining · C10 O(log N) · C11 O(1) · C12 O(n) · C13 O(log n) · C14 O(log n) each · C15 n + 1 · C16 O(n) · C17 O(log_d n) · C18 O(log n); O(1) · C19 O(n + k log n) · C20 less than

## Part D

**D1.** 10→3. 17→3 taken→**4**. 24→3, 4 taken→**5**. 3→3, 4, 5 taken→**6**. 31→3…6 taken, wraps around→**0**.

| 0 | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| 31 | | | 10 | 17 | 24 | 3 |

This is primary clustering: every key piles into one run.

**D2.** 18→5. 41→2. 31→5 taken, +1→**6**. 54→2 taken, +1→**3**. 28→2, 3 taken, +4→**6** taken, +9→11 → **11**. 44→5, 6 taken, +4→**9**. 15→2, 3 taken, +4→6 taken, +9→11 taken, +16→18 mod 13 = 5 taken, +25→27 mod 13 = **1**.

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| | 15 | 41 | 54 | | 18 | 31 | | | 44 | | 28 | |

**D3.**

| k | h(k) | d2(k) | probes | final |
|---|---|---|---|---|
| 18 | 5 | 3 | 5 | 5 |
| 41 | 2 | 1 | 2 | 2 |
| 22 | 9 | 6 | 9 | 9 |
| 44 | 5 | 5 | 5, 10 | 10 |
| 59 | 7 | 4 | 7 | 7 |
| 32 | 6 | 3 | 6 | 6 |
| 31 | 5 | 4 | 5, 9, 0 | 0 |
| 73 | 8 | 4 | 8 | 8 |

Table: [31, –, 41, –, –, 18, 32, 59, 73, 22, 44, –, –]

**D4.** Chains: 0 → 5. 1 → empty. 2 → 12 → 7 → 22 → 17. 3 → 3. 4 → empty. Load factor α = 6/5 = **1.2**. With chaining α can exceed 1.

**D5.** (a) 42→2, 12→**3**, 22→**4**, 9→9, 19→9 taken, wraps→**0**.

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 |
|---|---|---|---|---|---|---|---|---|---|
| 19 | | 42 | 12 | 22 | | | | | 9 |

(b) Cell 3 becomes "A". Searching 22 probes 2, 3 (A, keep going), 4 → **3 probes**.
(c) 32 → cell 2 is taken, cell 3 is available → **cell 3**.

**D6.** 0→0. 7→0, then 1 → **1**. 14→0, 1, then 4 → **4**. 21→0, 1, 4, then 9 mod 7 = **2**. 28: the probe offsets j² mod 7 for j = 0…6 are 0, 1, 4, 2, 2, 4, 1, so only cells **0, 1, 2, 4** are ever tried and all are full. **The insertion fails although cells 3, 5 and 6 are empty.** That is why quadratic probing "is not guaranteed to find an empty bucket".

**D7.** 10→10, 17→6, 24→2, 3→3, 31→9. No collisions. Load factor goes from 5/7 ≈ **0.71** to 5/11 ≈ **0.45**.

**D8.** 15 → T1[1]. 22 → T1[1] is taken, so 22 goes in and 15 moves to T2[⌊15/7⌋ mod 7 = 2]. 8 → T1[1], evicting 22 to T2[⌊22/7⌋ mod 7 = 3]. 29 → T1[1], evicting 8 to T2[⌊8/7⌋ mod 7 = 1].
T1 = [–, **29**, –, –, –, –, –]. T2 = [–, **8**, **15**, **22**, –, –, –].

**D9.** α = 0.5: ½(1 + 2) = **1.5**. α = 0.75: ½(1 + 4) = **2.5**. α = 0.9: ½(1 + 10) = **5.5**.

**D10.** After inserts: **[1, 4, 2, 10, 8, 15, 6]**.
removeMin → returns 1, 6 moves to the root and downheaps: **[2, 4, 6, 10, 8, 15]**.
removeMin → returns 2, 15 moves to the root and downheaps: **[4, 8, 6, 10, 15]**.

**D11.** (a) 3 goes to index 6. Its parent (index 3) is 6 → swap. Its new parent (index 1) is 2 → stop. **[2, 5, 3, 9, 7, 6]**.
(b) 7 replaces the root: [7, 5, 6, 9]. The smaller child is 5 → swap → [5, 7, 6, 9]. 7's child 9 is larger → stop. **[5, 7, 6, 9]**.

**D12.** (a) **Yes**: 2 ≤ 5, 6 and 5 ≤ 9, 7. (b) **No**: 2 at index 5 is smaller than its parent 5 at index 2. (c) **Yes**: 1 ≤ 3, 2; 3 ≤ 7, 4; 2 ≤ 5, 6.

**D13.** n = 8. i = 4 (12): child 20, ok. i = 3 (4): children 7 and 23, ok. i = 2 (15): smaller child 6 → swap. i = 1 (16): smaller child 4 → swap, then smaller child 7 → swap.
**[4, 6, 7, 12, 15, 16, 23, 20]**

**D14.** i = 3 (5): children 8, 6, ok. i = 2 (7): smaller child 1 → swap → [9, 1, 5, 3, 7, 8, 6]. i = 1 (9): smaller child 1 → swap, then smaller child 3 → swap.
**[1, 3, 5, 9, 7, 8, 6]**

**D15.** Index 5 has children **10 and 11** and parent **⌊5/2⌋ = 2**. A heap of 1,000 keys has height **⌊log₂ 1000⌋ = 9**.

**D16.** Children at **4i + 1, 4i + 2, 4i + 3, 4i + 4**; parent at **⌊(i − 1)/4⌋**. Levels hold 1, 4, 16, 64, so depths 0–3 hold 85 keys and the remaining 15 go at depth 4 → **height 4**. A binary heap with 100 keys has height 6.

**D17.**

| PQ implementation | insert | min | removeMin |
|---|---|---|---|
| Sorted list | O(n) | O(1) | O(1) |
| Unsorted list | O(1) | O(n) | O(n) |
| Heap | O(log n) | O(1) | O(log n) |

**D18.** Naive: sort in O(n log n) ≈ 20 million comparisons. Heap: O(n + k log n) ≈ 1,000,000 + 20 · 20 = about 1 million. The heap approach wins because k is much smaller than n.

**D19.** Every word is looked up: not found → insert with 1, found → add 1. Words with count > 1: **(to, 3), (be, 2)**. All others have count 1.

**D20.** In bottom-up construction most nodes are near the bottom, where downheap is short. About n/2 nodes need 0 swaps, n/4 need at most 1, n/8 at most 2, and so on. The total n(0/2 + 1/4 + 2/8 + 3/16 + …) is at most n, so it is **O(n)**. Doing n separate inserts can cost up to log n swaps each, which gives **O(n log n)**.
