# COMP 8547 Mid-Term I: Practice Questions

142 questions in the same format as the real exam: MCQ Level I, MCQ Level II (scenarios), short answer Level I, short answer Level II (hands-on). The answer key is at the bottom. Try each section before looking.

Notation for trees: `9B[4R[2B,6B],15B]` means node 9 (black) with left child 4 (red) and right child 15 (black); `-` means an empty child.

---

## Part A. MCQ Level I

**A1.** Which function grows fastest? (a) n³ (b) n log n (c) 2ⁿ (d) n²

**A2.** The load factor of a hash table with n entries and N buckets is: (a) N/n (b) n/N (c) n·N (d) n − N

**A3.** Linear probing mainly suffers from: (a) secondary clustering (b) primary clustering (c) stack overflow (d) unbounded table growth

**A4.** In an array-based heap with the root at index 1, the children of the node at index i are at: (a) i+1, i+2 (b) 2i−1, 2i (c) 2i, 2i+1 (d) i/2, i/2+1

**A5.** Bottom-up heap construction on n keys runs in: (a) O(log n) (b) O(n) (c) O(n log n) (d) O(n²)

**A6.** Which search tree stores no height, balance or colour information? (a) AVL (b) red-black (c) splay (d) (2,4)

**A7.** An inorder traversal of a binary search tree visits keys in: (a) level order (b) decreasing order (c) increasing order (d) random order

**A8.** Which sorting algorithm is stable? (a) quicksort (b) heapsort (c) selection sort (d) bucket sort

**A9.** Java's HashMap resolves collisions using: (a) linear probing (b) double hashing (c) separate chaining (d) cuckoo hashing

**A10.** Java's TreeMap is implemented as: (a) AVL tree (b) red-black tree (c) splay tree (d) B-tree

**A11.** Which is **not** a red-black tree property? (a) the root is black (b) a red node's children are black (c) the heights of every node's two subtrees differ by at most 1 (d) all leaves have the same black depth

**A12.** f(n) is o(g(n)) when the inequality f(n) < c·g(n) holds for: (a) some c > 0 (b) every c > 0 (c) c = 1 only (d) no c

**A13.** Per the slides, Big-Omega is associated with which case? (a) worst (b) average (c) best (d) amortized

**A14.** In double hashing with d2(k) = q − (k mod q), which is required? (a) q > N (b) q and N prime, q < N (c) N even (d) d2(k) may be 0

**A15.** A newly inserted (non-root) node in a red-black tree is coloured: (a) black (b) red (c) the colour of its parent (d) double black

**A16.** A limitation of experimental analysis is that it: (a) ignores input size (b) needs a working implementation and depends on hardware and language (c) cannot measure running time (d) only works for sorting

**A17.** In the RAM model, one primitive operation (assignment, indexing, method call) takes: (a) O(log n) (b) constant time (c) O(n) (d) time that depends on the input

**A18.** An abstract data type (ADT) is: (a) a Java class (b) a set of objects together with a set of operations (c) a memory layout (d) a sorting algorithm

**A19.** In the Map ADT, put(k, v) when key k is already in the map returns: (a) null (b) the new value v (c) the old value of k (d) an error

**A20.** Quadratic probing avoids primary clustering but causes: (a) secondary clustering (b) stack overflow (c) longer chains (d) duplicate keys

**A21.** Cuckoo hashing handles a collision by: (a) adding to a linked list (b) displacing the occupant into a second table (c) using a directory of disk blocks (d) probing i + j²

**A22.** Extendible hashing is designed to: (a) give O(1) worst case in RAM (b) search huge disk-based data in at most two disk accesses (c) avoid hash functions (d) keep keys sorted

**A23.** Which is a collection (forest) of heaps rather than a single heap? (a) leftist heap (b) skew heap (c) binomial queue (d) d-heap

**A24.** In a Fibonacci heap, removeMin takes amortized: (a) O(1) (b) O(log n) (c) O(n) (d) O(n log n)

**A25.** In Java's PriorityQueue, the method that removes and returns the minimum is: (a) pop() (b) poll() (c) removeFirst() (d) take()

**A26.** Which traversal evaluates an arithmetic expression tree? (a) preorder (b) inorder (c) postorder (d) level order

**A27.** An Euler tour visits each internal node: (a) once (b) twice (c) three times (d) log n times

**A28.** The depth property of a (2,4) tree says: (a) every node has 4 children (b) all external nodes have the same depth (c) depths differ by at most 1 (d) the root has depth 1

**A29.** When a key is deleted from a splay tree, which node is splayed? (a) the deleted node (b) the root (c) the parent of the removed node (d) none

**A30.** Java's Arrays.sort on primitive arrays uses: (a) heapsort (b) dual-pivot quicksort (c) radix sort (d) insertion sort

**A31.** With Hibbard's gap sequence (1, 3, 7, …, 2ᵏ − 1), Shellsort's worst case is: (a) O(n) (b) O(n log n) (c) O(n^1.5) (d) O(n²)

**A32.** Quickselect follows which design principle? (a) greedy (b) prune-and-search (c) dynamic programming (d) brute force

---

## Part B. MCQ Level II (scenarios)

**B1.** You are building a spell checker that only needs "is this word in the dictionary?" as fast as possible. Best structure? (a) sorted array (b) AVL tree (c) hash table (d) heap

**B2.** A course system must list students in ID order and answer "all IDs between 1000 and 2000" with guaranteed O(log n) updates. Best choice? (a) hash table (b) red-black tree (c) unsorted array (d) binary heap

**B3.** You must sort 50 GB of log records on a machine with 8 GB of RAM. Which algorithm fits best? (a) quicksort (b) heapsort (c) mergesort (d) insertion sort

**B4.** Sort 200,000 exam scores, each an integer from 0 to 100. Fastest choice? (a) counting sort (b) quicksort (c) mergesort (d) shellsort

**B5.** An operating system must always run the highest-priority ready job and jobs arrive constantly. Which structure? (a) stack (b) heap-based priority queue (c) sorted linked list (d) hash table

**B6.** An embedded device has almost no spare memory and needs guaranteed O(n log n) sorting. Choose: (a) mergesort (b) quicksort (c) heapsort (d) counting sort

**B7.** A music app stores songs in a search tree. A few songs are played far more often than all others. Which tree adapts best? (a) BST (b) AVL (c) splay tree (d) (2,4) tree

**B8.** You need the median of 10 million unsorted numbers once, as fast as possible on average. Use: (a) mergesort then pick the middle (b) quickselect (c) build an AVL tree (d) bubble sort

**B9.** A read-heavy dictionary is built once and then searched millions of times with almost no updates. Which balanced tree gives the shortest searches? (a) AVL (b) red-black (c) splay (d) unbalanced BST

**B10.** Employees are already sorted by name. You now sort them by department and need names to stay alphabetical within each department. Choose: (a) quicksort (b) heapsort (c) mergesort (d) selection sort

**B11.** A list of 30 items is already almost sorted. Which simple algorithm is fastest here? (a) selection sort (b) insertion sort (c) heapsort (d) radix sort

**B12.** Quicksort always using the last element as pivot is run on an already-sorted array of n items. Running time? (a) O(n) (b) O(n log n) (c) O(n²) (d) O(log n)

**B13.** A financial analyst needs, for every day i of 10 years of prices, the average of days 0..i. Best approach? (a) recompute each average from scratch (b) keep a running sum (c) sort the prices first (d) build a heap

**B14.** Given 1 million daily gains and losses, find the contiguous period with the largest total gain, as fast as possible. Use: (a) cubic MCSS (b) quadratic MCSS (c) divide-and-conquer MCSS (d) linear MCSS

**B15.** You must count how often each word appears across thousands of web pages. Best structure? (a) sorted array (b) hash table keyed by word (c) min-heap (d) linked list

**B16.** A database index on disk holds millions of records and must support sorted scans and range queries with as few disk reads as possible. Choose: (a) in-memory hash table (b) B-tree / multi-way search tree (c) splay tree (d) unsorted array

**B17.** Sort 1 million 9-digit student IDs. Fastest choice? (a) counting sort with N = 10⁹ (b) radix sort digit by digit (c) bubble sort (d) selection sort

**B18.** A linear-probing hash table has reached load factor 0.9 and searches are getting slow. Best fix? (a) switch to quadratic probing in place (b) rehash into a larger (prime-sized) table (c) sort the table (d) delete half the keys

**B19.** A system does very frequent insertions and deletions and needs guaranteed O(log n) per operation with few rotations. Choose: (a) AVL tree (b) red-black tree (c) splay tree (d) unbalanced BST

**B20.** Find the 100 smallest values among 1,000,000 unsorted values. Best approach? (a) mergesort everything (b) build a heap in O(n), then 100 removeMins (c) 100 passes of bubble sort (d) insert all into an unbalanced BST

**B21.** Sort a singly linked list of 5 million records (no random access). Choose: (a) mergesort (b) heapsort (c) in-place quicksort (d) shellsort

**B22.** An emergency room always treats the most urgent patient first; urgency is decided by a custom rule. In Java you would use: (a) HashMap (b) PriorityQueue with a Comparator (c) TreeSet with no comparator (d) ArrayList sorted after every insert

---

## Part C. Short answer Level I

C1. Worst-case time to search a BST with n keys is ______.
C2. Expected time for search in a hash table with a low load factor is ______.
C3. Inserting into a binary heap takes ______ time.
C4. Worst-case running time of mergesort is ______.
C5. A proper binary tree has 7 internal nodes. It has ______ external nodes.
C6. The recommended load factor for open addressing is below ______.
C7. Radix sort on d-digit keys in range [0, N−1] runs in ______.
C8. The three splaying operations are ______, ______ and ______.
C9. The maximum number of children of a node in a (2,4) tree is ______.
C10. The time complexity of `for (i = 1; i <= n; i *= 2) count++;` is ______.
C11. The linear-time MCSS algorithm runs in ______.
C12. Average running time of quickselect is ______.
C13. The minimum number of comparisons to find the smallest of n keys is ______.
C14. The minimum number of comparisons to find both the min and max of n keys is ______.
C15. Selecting the k smallest keys with a heap takes ______.
C16. The default load factor of Java's HashMap is ______.
C17. Worst-case search in a splay tree is ______.
C18. The recurrence for binary search is T(n) = ______.
C19. In an AVL tree, how many restructure operations at most does one insertion need? ______
C20. Height of a heap storing n keys is ______.
C21. Number of primitive operations of arrayMax on n elements: T(n) = ______.
C22. Running time of quadPrefixAve is ______; of linearPrefixAve is ______.
C23. The divide-and-conquer MCSS recurrence is T(n) = ______, which solves to ______.
C24. The cubic MCSS algorithm runs in ______.
C25. Expected probes for a search with linear probing at load factor α: ______.
C26. Default initial capacity of Java's HashMap: ______.
C27. A heap with n keys stored in an array needs an array of size ______ (index 0 unused).
C28. Height of a d-heap with n keys: ______.
C29. A proper binary tree with e external nodes has ______ nodes in total.
C30. Minimum number of keys of an AVL tree of height h satisfies n(h) > ______.
C31. The height of a red-black tree is at most ______ times the height of its associated (2,4) tree.
C32. Bucket sort on n entries with keys in [0, N − 1] runs in ______.
C33. Lower bound on comparisons to find the two smallest of n keys: ______.
C34. Number of comparisons quicksort makes in its worst case: ______.
C35. Probability that a quicksort call is "good" (both sides smaller than 3s/4): ______.
C36. Lower bound on comparisons to find the median of n keys: ______.
C37. In double hashing with d2(k) = q − (k mod q), the possible values of d2 are ______.
C38. In linear probing, a removed cell is marked with ______ so searches continue past it.

---

## Part D. Short answer Level II (hands-on)

**D1.** Find an upper bound for f(n) = 2n + 10. Give c and n0.

**D2.** Show that f(n) = 3n² + 5n + 2 is O(n²). Give c and n0.

**D3.** Give the Big-O of each fragment:
```java
// (a)
for (i = 1; i <= n; i++)
  for (j = i; j <= n; j++) k++;
// (b)
for (i = n; i > 0; i /= 2)
  for (j = 0; j < i; j++) k++;
// (c)
for (i = 1; i <= n; i++)
  for (j = 1; j < n; j *= 3) k++;
```

**D4.** Algorithm A uses 20·n·log₂n operations, algorithm B uses 2n². For which n0 does A become faster? Which do you use for n = 10,000?

**D5.** N = 11, h(k) = k mod 11, **linear probing**. Insert 22, 1, 13, 11, 24, 33, 18, 42, 31. Show the final table.

**D6.** Same table size and hash, **quadratic probing**. Insert 22, 1, 13, 11, 24, 33, 18, 42. Show the table. Then try to insert 31: what happens?

**D7.** N = 13, h(k) = k mod 13, **double hashing** with d2(k) = 7 − (k mod 7). Insert 14, 27, 40, 5, 18, 31, 44. Show d2 and the probes for each key and the final table.

**D8.** Insert 15, 9, 20, 4, 11, 2, 7 into an empty min-heap. Write the array (index 1 onward). Then do removeMin twice and write the array after each.

**D9.** Insert 50, 30, 70, 20, 40, 60, 80, 35, 45 into an empty BST. Write the preorder and postorder traversals. Then delete 30, then 50 (use the inorder successor) and write the preorder.

**D10.** Insert 10, 20, 30, 40, 50, 25 into an empty AVL tree. Name each rotation and write the final preorder.

**D11.** AVL tree: `20[10[5,-],30[25,40[35,50]]]`. Delete 5 and rebalance. Write the preorder.

**D12.** AVL tree: `44[17[-,32],78[50[48,62],88]]`. (a) Insert 54 and rebalance. (b) Starting again from the original tree, insert 56, then delete 44 (inorder successor). Write each result.

**D13.** (Exam example) Red-black tree: `9B[4R[2B,6B[-,7R]],15B[12R,21R]]`. Insert 5 and delete 15. Write the in-order traversal as KEY(colour).

**D14.** Same starting tree as D13, each part separately: (a) insert 8, (b) insert 13, (c) delete 2, (d) delete 9. Write each in-order traversal with colours.

**D15.** Insert 10, 20, 30, 15, 25, 5, 1 into an empty red-black tree. Write the in-order traversal with colours. Then delete 1 and then 5; write the result.

**D16.** Splay tree (BST): `6[2[1,4],9[8,-]]`. Insert 3 and splay. Name the operations and write the preorder.

**D17.** Build a BST by inserting 50, 30, 70, 20, 40, 60, 80, 35 (no splaying). Now search for 35 in it as a splay tree. Name the operations and write the preorder.

**D18.** In-place quicksort (slides version, pivot = last element) on `40 70 10 90 30 60 20 50`. Show the array after the first partition and where the pivot lands.

**D19.** Mergesort `38 27 43 3 9 82 10 15`. Show every merge.

**D20.** Radix sort (LSD) `170 45 75 90 802 24 2 66`. Show the list after each pass.

**D21.** Counting sort `4 1 3 4 0 2 1 4` with keys in [0, 4]. Show the counter array and the output.

**D22.** Find the MCSS of A = 3, 4, −7, 3, 6, −3, 2, 8, −1 and the subsequence that gives it.

**D23.** Quickselect the 3rd smallest of `12 3 5 7 4 19 26`, always choosing the first element as pivot. Show each call.

**D24.** Sort by growth rate, slowest first: 12n², 3n, 0.5 log n, n log n, 2n³.

**D25.** For f(n) = 2n² + 3, say true or false: (a) O(n) (b) O(n¹⁰) (c) Ω(1) (d) Θ(n²) (e) o(n^(9/4)) (f) ω(√n) (g) o(n²).

**D26.** True or false: (a) if f is O(g) then f is Ω(g); (b) if f is O(g) then g is Ω(f); (c) if f is O(g) and Ω(g) then f is Θ(g); (d) if f is o(g) then f is O(g); (e) if f is o(g) then g is ω(f); (f) if f is Θ(g) then f is o(g).

**D27.** Give the Big-O of each fragment:
```java
// (a)
for (i = 1; i * i <= n; i++) count++;
// (b)
for (i = 0; i < n; i++)
  for (j = 0; j < i * i; j++) count++;
// (c)
for (i = 1; i <= n; i++)
  if (i % 2 == 0)
    for (j = 1; j <= n; j++) count++;
// (d)
while (n > 1) n = n / 3;
// (e)
for (i = 0; i < N; i++) a++;
for (j = 0; j < M; j++) b++;
```

**D28.** (Slide example) N = 13, h(k) = k mod 13, linear probing. Insert 18, 41, 22, 44, 59, 32, 31, 73. (a) Show the table. (b) Remove 31. How many cells are probed when searching for 73? (c) Now insert 70. Where does it go?

**D29.** Rehash the table from D28(a) into N = 23 with h(k) = k mod 23 (linear probing, insert in the original order). Show where each key lands and the load factor before and after.

**D30.** Cuckoo hashing with two tables of size 5: h1(k) = k mod 5, h2(k) = ⌊k/5⌋ mod 5. Insert 20, 50, 53, 75 (always try Table 1 first). Show both tables. Then explain what happens when you insert 100.

**D31.** What is the height of a 3-heap holding 100 keys? Of a binary heap holding 100 keys?

**D32.** A proper binary tree has 15 nodes. How many are external and internal? What are its minimum and maximum possible heights?

**D33.** For the expression tree of ((2 × (a − 1)) + (3 × b)), write the preorder and postorder traversals and evaluate it for a = 5, b = 4.

**D34.** Binary search on S = 0 1 3 4 5 7 8 9 11 14 16 18 19 (indices 0–12, mid = ⌊(low + high)/2⌋). List the keys compared when searching for 7, then for 15.

**D35.** In-place heapsort of 5, 3, 8, 1, 4 in increasing order (max-heap, array index 0 = root). Show the array after phase 1 and after each removal in phase 2.

**D36.** Insert 50, 40, 30, 45, 47, 46 into an empty AVL tree. Name each rotation and give the final preorder.

**D37.** Insert 15, 20, 24, 10, 13, 7, 30, 36, 25 into an empty AVL tree. Give the tree, then delete 24 and then 20 (inorder successor) and give the final preorder.

**D38.** Insert 3, 2, 1, 4, 5, 6, 7 into an empty AVL tree. Name each rotation and draw the final tree.

**D39.** (Slide example) Red-black tree `6B[3R,8R]`. (a) Insert 4. (b) Then delete 8. Give the tree after each step.

**D40.** Insert 41, 38, 31, 12, 19, 8 into an empty red-black tree. Give the in-order traversal with colours. Then delete 41 and give it again.

**D41.** Insert 5, 10, 15, 20, 25, 30 (in that order) into an empty red-black tree. Give the in-order traversal with colours.

**D42.** Into an empty splay tree insert 10, 20, 30, 40 (splaying after each insert). Then search 10, then search 30. Give the tree after each search and name the operations.

**D43.** (Slide example) Run the slides' in-place quicksort on 85 24 63 45 17 31 96 50. List each partition call: the range, the pivot and the array after it.

**D44.** Merge A = 12 19 24 42 62 with B = 18 40 56 61. How many key comparisons are made?

**D45.** (Slide example) Bucket sort the entries (7,d) (1,c) (3,a) (7,g) (3,b) (7,e) with keys in [0, 9]. Give the output and say why the order of the 7s matters.

**D46.** (Slide example) Radix sort 329 457 657 839 436 720 355. Show each pass.

**D47.** Divide-and-conquer MCSS on A = −3, 10, −2, 11, −1, 2, −3, split into −3, 10, −2, 11 and −1, 2, −3. Give the MCSS of each half, the max left-border sum, the max right-border sum and the final answer. Also give the MCSS of 12, −5, −6, −4, 3 and of −7, −10, −1, −3.

**D48.** For n = 16 keys, give the minimum number of comparisons needed to find (a) the smallest key, (b) the two smallest keys, (c) both the min and the max.

**D49.** Give 8 integers that cause the worst case for the slides' in-place quicksort (last-element pivot). How many comparisons does it make? Do mergesort and heapsort slow down on the same input?

**D50.** What is the running time of mergesort, quicksort and heapsort when all n elements are equal?

---
---

# Answer key

## Part A
A1 c · A2 b · A3 b · A4 c · A5 b · A6 c · A7 c · A8 d · A9 c · A10 b · A11 c (that is the AVL property) · A12 b · A13 c · A14 b · A15 b
A16 b · A17 b · A18 b · A19 c · A20 a · A21 b · A22 b · A23 c · A24 b · A25 b · A26 c · A27 c · A28 b · A29 c · A30 b · A31 c · A32 b

## Part B
- B1 **c** hash table: O(1) expected lookup, no ordering needed.
- B2 **b** red-black tree: ordered traversal and range queries with O(log n) worst case. A hash table loses order.
- B3 **c** mergesort: sequential access, works as an external sort on chunks.
- B4 **a** counting sort: N = 101 keys, O(n + N) = O(n).
- B5 **b** heap: insert and removeMin (or removeMax) in O(log n).
- B6 **c** heapsort: in-place and O(n log n) in every case. Mergesort needs O(n) extra memory; quicksort can hit O(n²).
- B7 **c** splay tree: hot songs stay near the root.
- B8 **b** quickselect: O(n) average, versus O(n log n) to sort.
- B9 **a** AVL: stricter balance means a lower tree than red-black, so searches are shorter. Red-black wins when updates are frequent.
- B10 **c** mergesort: stable.
- B11 **b** insertion sort: O(n) best case on nearly sorted input.
- B12 **c** O(n²): every pivot is the maximum, so one side always has n − 1 items. Fix with a random or median pivot.
- B13 **b** running sum: linearPrefixAve is O(n) versus O(n²) for recomputing.
- B14 **d** linear MCSS: O(n). Divide and conquer is O(n log n); quadratic and cubic are far slower.
- B15 **b** hash table: O(1) expected lookup and increment per word (the slides' word-frequency application).
- B16 **b** B-tree / multi-way search tree: wide nodes keep the tree shallow, so few disk reads, and keys stay ordered for range scans. A hash table loses order.
- B17 **b** radix sort: d = 9 digits, N = 10 per digit, O(d(n + N)) = O(n). Counting sort would need 10⁹ counters.
- B18 **b** rehash: lowers α so expected search goes back to O(1). Ideal α is below 0.5.
- B19 **b** red-black tree: O(log n) worst case with fewer rotations than AVL on updates.
- B20 **b** heap: O(n + k log n) with k = 100, much less than O(n log n).
- B21 **a** mergesort: needs only sequential access, so it suits linked lists.
- B22 **b** PriorityQueue with a Comparator: a heap ordered by your rule.

## Part C
C1 O(n) · C2 O(1) · C3 O(log n) · C4 O(n log n) · C5 8 (e = i + 1) · C6 0.5 · C7 O(d(n + N)) · C8 zig, zig-zig, zig-zag · C9 4 · C10 O(log n) · C11 O(n) · C12 O(n) · C13 n − 1 · C14 3n/2 − 2 · C15 O(n + k log n) · C16 0.75 · C17 O(n) · C18 T(n/2) + 1 (→ O(log n)) · C19 one (one trinode restructure) · C20 O(log n), exactly ⌊log₂ n⌋
C21 8n − 3 · C22 O(n²); O(n) · C23 2T(n/2) + n; O(n log n) · C24 O(n³) · C25 ½(1 + 1/(1 − α)) · C26 16 · C27 n + 1 · C28 O(log_d n) · C29 2e − 1 · C30 2^(h/2 − 1) · C31 two · C32 O(n + N) · C33 n + ⌈log n⌉ − 2 · C34 n(n − 1)/2 · C35 ½ · C36 3n/2 − O(log n) · C37 1, 2, …, q · C38 "A" (available)

## Part D

**D1.** 2n + 10 ≤ cn ⇔ (c − 2)n ≥ 10. With **c = 3, n0 = 10**: 2n + 10 ≤ 3n for all n ≥ 10. So f(n) is **O(n)**.

**D2.** Take **c = 4**: need 3n² + 5n + 2 ≤ 4n² ⇔ n² − 5n − 2 ≥ 0. n = 5 gives −2 (fails), n = 6 gives 4 (holds), so **n0 = 6**. (Also valid: c = 10, n0 = 1, since 3n² + 5n + 2 ≤ 3n² + 5n² + 2n² for n ≥ 1.)

**D3.** (a) n + (n−1) + … + 1 = n(n+1)/2 → **O(n²)**. (b) n + n/2 + n/4 + … ≤ 2n → **O(n)** (not n log n). (c) n × log₃ n → **O(n log n)**.

**D4.** A is faster when 20 n log n < 2n² ⇔ 10 log₂ n < n. n = 58: 10·5.86 = 58.6 > 58 (no); n = 59: 10·5.88 = 58.8 < 59 (yes). **n0 = 59**. For n = 10,000 use **A**.

**D5.** 22→0, 1→1, 13→2, 11 (0 taken)→3, 24 (2,3 taken)→4, 33 (0–4 taken)→5, 18→7, 42→9, 31 (9 taken)→10.

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|---|
| 22 | 1 | 13 | 11 | 24 | 33 | | 18 | | 42 | 31 |

Note the long primary cluster in cells 0–5.

**D6.** 22→0, 1→1, 13→2, 11: 0, 1, **4**. 24: 2, **3**. 33: 0, 1, 4, **9**. 18→7. 42: 9, **10**.

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---|---|---|---|---|---|---|---|---|---|---|
| 22 | 1 | 13 | 24 | 11 | | | 18 | | 33 | 42 |

Insert 31 (home 9): probes 9 + j² mod 11 for j = 0…10 give 9, 10, 2, 7, 3, 1, 1, 3, 7, 2, 10, all occupied. Cells 5, 6, 8 are never probed, so **the insertion fails even though the table has empty cells**. This is why quadratic probing "is not guaranteed to find an empty bucket" (keep α < 0.5 or rehash).

**D7.**

| k | h(k) | d2(k) | probes | final |
|---|---|---|---|---|
| 14 | 1 | 7 | 1 | 1 |
| 27 | 1 | 1 | 1, 2 | 2 |
| 40 | 1 | 2 | 1, 3 | 3 |
| 5 | 5 | 2 | 5 | 5 |
| 18 | 5 | 3 | 5, 8 | 8 |
| 31 | 5 | 4 | 5, 9 | 9 |
| 44 | 5 | 5 | 5, 10 | 10 |

Final table: [ –, 14, 27, 40, –, 5, –, –, 18, 31, 44, –, – ]

**D8.** Inserts: 15 | 9 swaps up | 20 | 4 swaps up twice | 11 | 2 swaps to root | 7.
Heap: **[2, 9, 4, 15, 11, 20, 7]**
removeMin → 2, move 7 to root, downheap: **[4, 9, 7, 15, 11, 20]**
removeMin → 4, move 20 to root, downheap: **[7, 9, 20, 15, 11]**

**D9.** Tree `50[30[20,40[35,45]],70[60,80]]`.
Preorder: 50 30 20 40 35 45 70 60 80. Postorder: 20 35 45 40 30 60 80 70 50.
Delete 30 (two children, successor 35): preorder **50 35 20 40 45 70 60 80**.
Delete 50 (successor 60): preorder **60 35 20 40 45 70 80**.

**D10.** Insert 30 → 10 unbalanced, **single left rotation** → `20[10,30]`. Insert 50 → 30 unbalanced, **single left rotation** at 30 → `20[10,40[30,50]]`. Insert 25 (left of 30) → 20 unbalanced, path right-left (zig-zag) → **double rotation (right at 40, then left at 20)** → `30[20[10,25],40[-,50]]`.
Preorder: **30 20 10 25 40 50**.

**D11.** After removing 5, node 20 has left height 1 and right height 3. y = 30, its taller child x = 40 (same side) → **single left rotation** at 20 → `30[20[10,25],40[35,50]]`. Preorder: **30 20 10 25 40 35 50**.

**D12.** (a) 54 becomes the left child of 62; walking up, 78 is the first unbalanced node (left height 3, right 1); z = 78, y = 50, x = 62 (zig-zag) → double rotation → `44[17[-,32],62[50[48,54],78[-,88]]]`.
(b) After inserting 56: `44[17[-,32],62[50[48,56],78[-,88]]]`. Delete 44: successor 48 replaces it, 50 is still balanced → `48[17[-,32],62[50[-,56],78[-,88]]]`.

**D13.** Insert 5: left child of 6, parent black, stays red. Delete 15: successor 21 is copied up, the red leaf is removed, no fix-up. Tree `9B[4R[2B,6B[5R,7R]],21B[12R,-]]`.
**2(B) − 4(R) − 5(R) − 6(B) − 7(R) − 9(B) − 12(R) − 21(B)**
(If your instructor uses the inorder predecessor instead, the end becomes 12(B) − 21(R). The slides use the successor.)

**D14.**
- (a) Insert 8: right of 7, double red, uncle (left of 6) is black → **restructure** 6, 7, 8 → 7 black, 6 and 8 red.
  2(B) − 4(R) − 6(R) − 7(B) − 8(R) − 9(B) − 12(R) − 15(B) − 21(R)
- (b) Insert 13: right of 12, double red, uncle 21 is red → **recolour** 12 and 21 black, 15 red; 15's parent 9 is black, done.
  2(B) − 4(R) − 6(B) − 7(R) − 9(B) − 12(B) − 13(R) − 15(R) − 21(B)
- (c) Delete 2: black leaf → double black. Sibling 6 is black with red child 7 → **Case 1 restructure** on 4, 6, 7: 6 takes the old parent's colour (red), 4 and 7 become black.
  4(B) − 6(R) − 7(B) − 9(B) − 12(R) − 15(B) − 21(R)
- (d) Delete 9: successor 12 (red leaf) is copied to the root and removed, no fix-up.
  2(B) − 4(R) − 6(B) − 7(R) − 12(B) − 15(B) − 21(R)

**D15.** Steps: 10B → 20R → 30 causes double red, uncle black → restructure → `20B[10R,30R]` → 15: uncle 30 red → recolour → `20B[10B[-,15R],30B]` → 25 red under 30 → 5 red under 10 → 1: double red under 5, uncle 15 red → recolour 5, 15 black and 10 red.
Tree `20B[10R[5B[1R,-],15B],30B[25R,-]]`
**1(R) − 5(B) − 10(R) − 15(B) − 20(B) − 25(R) − 30(B)**
Delete 1 (red leaf): just remove. Delete 5 (black leaf): double black; sibling 15 is black with no red children → **Case 2 recolour**: 15 red; the parent 10 was red, so make it black and stop.
Tree `20B[10B[-,15R],30B[25R,-]]` → **10(B) − 15(R) − 20(B) − 25(R) − 30(B)**

**D16.** 3 is inserted as the left child of 4. 4 is the right child of 2 → **zig-zag** → 3 takes 2's place with children 2 and 4. Now 3's parent is the root 6 → **zig** → 3 is the root.
Tree `3[2[1,-],6[4,9[8,-]]]`. Preorder: **3 2 1 6 4 9 8**.

**D17.** BST `50[30[20,40[35,-]],70[60,80]]`. 35 is the left child of 40, which is the right child of 30 → **zig-zag** → `35[30[20,-],40]` under 50. Then 35's parent is the root → **zig**.
Tree `35[30[20,-],50[40,70[60,80]]]`. Preorder: **35 30 20 50 40 70 60 80**.

**D18.** Pivot 50. l stops at 70, r stops at 20 → swap → `40 20 10 90 30 60 70 50`. l stops at 90, r stops at 30 → swap → `40 20 10 30 90 60 70 50`. l stops at 90 (index 4), r passes it → stop. Swap S[4] with pivot:
**`40 20 10 30 50 60 70 90`**, pivot at index 4. Recurse on [0..3] and [5..7].

**D19.**
- [38] + [27] → 27 38; [43] + [3] → 3 43; [27 38] + [3 43] → 3 27 38 43
- [9] + [82] → 9 82; [10] + [15] → 10 15; [9 82] + [10 15] → 9 10 15 82
- [3 27 38 43] + [9 10 15 82] → **3 9 10 15 27 38 43 82**

**D20.**
- Ones digit: 170 90 802 2 24 45 75 66
- Tens digit: 802 2 24 45 66 170 75 90
- Hundreds digit: **2 24 45 66 75 90 170 802**

(Each pass must be stable: 802 stays before 2 in pass 2 because it was before it after pass 1.)

**D21.** C = [1, 2, 1, 1, 3] for keys 0–4. Output: **0 1 1 2 3 4 4 4**. Time O(n + N).

**D22.** **MCSS = 16**, from 3, 6, −3, 2, 8 (indices 3–7). Linear algorithm trace of the running sum: 3, 7, 0, 3, 9, 6, 8, 16, 15; max = 16. (The prefix 3 + 4 − 7 = 0 resets the sum.)

**D23.** quickselect(S, 3), pivot 12: L = {3, 5, 7, 4}, E = {12}, G = {19, 26}. k = 3 ≤ |L| = 4 → recurse on L.
quickselect({3, 5, 7, 4}, 3), pivot 3: L = {}, E = {3}, G = {5, 7, 4}. k = 3 > |L| + |E| = 1 → recurse on G with k = 3 − 0 − 1 = 2.
quickselect({5, 7, 4}, 2), pivot 5: L = {4}, E = {5}. |L| = 1 < k = 2 ≤ |L| + |E| = 2 → return **5**.

**D24.** 0.5 log n < 3n < n log n < 12n² < 2n³. Constants don't change the order.

**D25.** (a) **F**, n² grows faster than n. (b) **T**. (c) **T**. (d) **T**. (e) **T**, n² grows strictly slower than n^2.25. (f) **T**, n² grows strictly faster than √n. (g) **F**, the ratio tends to 2, not 0.

**D26.** (a) **F** (n is O(n²) but not Ω(n²)). (b) **T**. (c) **T**. (d) **T**. (e) **T**. (f) **F** (f is not strictly smaller than itself).

**D27.** (a) **O(√n)**: the loop stops when i² > n. (b) Σ i² ≈ n³/3 → **O(n³)**. (c) n/2 outer passes run the inner loop → **O(n²)**. (d) n is divided by 3 each time → **O(log n)**. (e) Independent sizes → **O(N + M)**.

**D28.** (a) 18→5, 41→2, 22→9, 44→5 taken→6, 59→7, 32→6, 7 taken→8, 31→5…9 taken→10, 73→8, 9, 10 taken→11.

| 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| | | 41 | | | 18 | 44 | 59 | 32 | 22 | 31 | 73 | |

(b) Cell 10 becomes "A". Searching 73 (home 8) probes 8, 9, 10 (A, keep going), 11 → found after **4 probes**. Without the marker the search would wrongly stop at 10.
(c) 70 mod 13 = 5. Cells 5–9 are full and 10 is available → **70 goes in cell 10** (an "A" cell can be reused on insert).

**D29.** 18→18, 41→18 taken→**19**, 22→22, 44→21, 59→13, 32→9, 31→8, 73→4. Load factor drops from 8/13 ≈ 0.62 to 8/23 ≈ 0.35, back under 0.5.

**D30.** 20 → T1[0]. 50 → T1[0] is taken, so 50 goes there and 20 moves to T2[⌊20/5⌋ mod 5 = 4]. 53 → T1[3]. 75 → T1[0], displacing 50 to T2[⌊50/5⌋ mod 5 = 0].
T1 = [75, –, –, 53, –], T2 = [50, –, –, –, 20].
Inserting 100: 100, 75 and 50 all have h1 = 0 and h2 = 0, so three keys fight over two cells. 100 kicks out 75 → 75 kicks out 50 from T2[0] → 50 kicks out 100 from T1[0] → … this **cycles forever**, so after a set number of displacements the table is **rebuilt** with new hash functions (or larger tables).

**D31.** 3-heap: full levels hold 1 + 3 + 9 + 27 = 40 keys, the remaining 60 fit at depth 4 → **height 4**. Binary heap: ⌊log₂ 100⌋ = **6**.

**D32.** n = 2e − 1 → **e = 8 external, i = 7 internal**. Minimum height log(n + 1) − 1 = **3** (perfect tree). Maximum height (n − 1)/2 = **7** (a "caterpillar").

**D33.** Preorder: **+ × 2 − a 1 × 3 b**. Postorder: **2 a 1 − × 3 b × +**. Value: 2 × (5 − 1) + 3 × 4 = 8 + 12 = **20**.

**D34.** 7: compares 8 (index 6), 3 (index 2), 5 (index 4), 7 (index 5) → **found after 4 comparisons**. 15: compares 8, 14, 18, 16 → low > high → **null**.

**D35.** Phase 1 (insert and upheap): [5] → [5, 3] → 8 swaps to the root [8, 3, 5] → [8, 3, 5, 1] → 4 swaps with 3 → **[8, 4, 5, 1, 3]**.
Phase 2: remove 8 → **[5, 4, 3, 1 | 8]**; remove 5 → **[4, 1, 3 | 5, 8]**; remove 4 → **[3, 1 | 4, 5, 8]**; remove 3 → **[1 | 3, 4, 5, 8]**. Sorted: 1 3 4 5 8.

**D36.**
- 30: 50 unbalanced, left-left → **single right rotation** at 50 → `40[30,50]`.
- 45: no rotation → `40[30,50[45,-]]`.
- 47: 50 unbalanced, left-right → **double rotation** → `40[30,47[45,50]]`.
- 46: 46 goes right of 45; the root 40 is unbalanced, path right-left (40 → 47 → 45) → **double rotation** → `45[40[30,-],47[46,50]]`.

Preorder: **45 40 30 47 46 50**.

**D37.** Rotations: left at 15 (after 24), left-right at 15 (after 13), right at 20 (after 7), left at 24 (after 36), right-left at 20 (after 25).
Tree: `13[10[7,-],24[20[15,-],30[25,36]]]`.
Delete 24 → successor 25 replaces it, no rotation. Delete 20 → its only child 15 moves up, still balanced.
Final `13[10[7,-],25[15,30[-,36]]]`, preorder **13 10 7 25 15 30 36**.

**D38.** 1: **single right** at 3 → `2[1,3]`. 4: none. 5: **single left** at 3 → `2[1,4[3,5]]`. 6: root 2 unbalanced → **single left** at 2 → `4[2[1,3],5[-,6]]`. 7: **single left** at 5.
Final: **`4[2[1,3],6[5,7]]`** (a perfect tree).

**D39.** (a) 4 goes right of 3. Double red with red uncle 8 → **recolour**: 3 and 8 become black, 6 would turn red but it is the root, so it stays black → `6B[3B[-,4R],8B]`.
(b) Deleting black leaf 8 → double black. Sibling 3 is black with red child 4 → **Case 1 restructure** on 3, 4, 6: 4 becomes the middle and takes the old parent's colour (black), 3 and 6 black → **`4B[3B,6B]`**.

**D40.** 31: restructure → `38B[31R,41R]`. 12: red uncle → recolour 31, 41 black. 19: right of 12, uncle black → restructure 12, 19, 31 → `19B[12R,31R]`. 8: red uncle 31 → recolour 12, 31 black, 19 red.
Tree `38B[19R[12B[8R,-],31B],41B]` → **8(R) − 12(B) − 19(R) − 31(B) − 38(B) − 41(B)**.
Delete 41: black leaf, sibling 19 is **red → Case 3 adjustment** (rotate 19 up, 19 black, 38 red). The new sibling 31 is black with black children → **Case 2 recolour**: 31 red; parent 38 was red → becomes black, stop.
Tree `19B[12B[8R,-],38B[31R,-]]` → **8(R) − 12(B) − 19(B) − 31(R) − 38(B)**.

**D41.** 15: restructure → `10B[5R,15R]`. 20: red uncle → recolour 5, 15 black. 25: uncle black → restructure 15, 20, 25 → `20B[15R,25R]`. 30: red uncle 15 → recolour 15, 25 black, 20 red.
Tree `10B[5B,20R[15B,25B[-,30R]]]` → **5(B) − 10(B) − 15(B) − 20(R) − 25(B) − 30(R)**.

**D42.** Each insert lands as the root's right child → **zig** → after 40: `40[30[20[10,-],-],-]` (a left chain).
Search 10: 10, 20, 30 are all left children → **zig-zig** (10 rises above 20 and 30), then **zig** with root 40 → **`10[-,40[20[-,30],-]]`**.
Search 30: 30 is the right child of 20, which is the left child of 40 → **zig-zag** → 30 with children 20 and 40, then **zig** with root 10 → **`30[10[-,20],40]`**.

**D43.**
1. [0..7] pivot 50 → `31 24 17 45 50 85 96 63`
2. [0..3] pivot 45 → `31 24 17 45` (45 already in place)
3. [0..2] pivot 17 → `17 24 31`
4. [1..2] pivot 31 → `24 31`
5. [5..7] pivot 63 → `63 96 85`
6. [6..7] pivot 85 → `85 96`

Sorted: **17 24 31 45 50 63 85 96**.

**D44.** 12<18, 18<19, 19<40, 24<40, 40<42, 42<56, 56<62, 61<62 → B is empty, then copy 62. **8 comparisons**. Result 12 18 19 24 40 42 56 61 62.

**D45.** Output: **(1,c) (3,a) (3,b) (7,d) (7,g) (7,e)**. Items with the same key keep their input order (d, g, e) because bucket sort is **stable**. Radix sort depends on that.

**D46.**
- Ones: 720 355 436 457 657 329 839
- Tens: 720 329 436 839 355 457 657
- Hundreds: **329 355 436 457 657 720 839**

**D47.** Left half MCSS = 19 (10 − 2 + 11). Right half MCSS = 2. Max left-border sum (ending at 11, going left) = **19**. Max right-border sum (starting at −1, going right) = **1** (−1 + 2). Spanning sum = 20. Answer = max(19, 2, 20) = **20** (10, −2, 11, −1, 2).
12, −5, −6, −4, 3 → **12**. −7, −10, −1, −3 → **0** (all negative).

**D48.** (a) n − 1 = **15**. (b) n + ⌈log n⌉ − 2 = 16 + 4 − 2 = **18**. (c) 3n/2 − 2 = **22**.

**D49.** Already sorted input, e.g. **1 2 3 4 5 6 7 8** (or reverse sorted): every pivot is the max or min, so the comparisons total n(n − 1)/2 = **28** → O(n²). Mergesort and heapsort stay **O(n log n)** on any input.

**D50.** Mergesort: **O(n log n)**, it always splits in half. Quicksort: the slides' in-place version moves every element ≤ pivot to the left, so each split is n − 1 / 0 → **O(n²)**; the L/E/G version puts everything in E → **O(n)**. Heapsort: upheap and downheap stop immediately when keys are equal → **O(n)**.
