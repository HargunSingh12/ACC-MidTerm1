# Chapter 4: Sorting

COMP 8547 Advanced Computing Concepts, Mid-Term I (Friday 23 October 2026). This page covers **only Chapter 4**: mergesort, quicksort, heapsort, the other comparison sorts, selection, bucket sort, radix sort and counting sort. Everything comes from the Chapter 4 slides. Practice questions are in [questions.md](questions.md).

**On this page**
1. [Sorting basics](#1-sorting-basics)
2. [Mergesort](#2-mergesort)
3. [Quicksort](#3-quicksort)
4. [Heapsort](#4-heapsort)
5. [Other comparison sorts](#5-other-comparison-sorts)
6. [Summary table](#6-summary-table)
7. [Selection](#7-selection)
8. [Bucket sort](#8-bucket-sort)
9. [Radix sort](#9-radix-sort)
10. [Counting sort](#10-counting-sort)
11. [Lower bound (not in the exam)](#11-lower-bound-not-in-the-exam)
12. [Sorting in Java](#12-sorting-in-java)
13. [The instructor's sample questions](#13-the-instructors-sample-questions)
14. [Last-minute checklist](#14-last-minute-checklist)

---

## 1. Sorting basics

- **Problem:** given S = s₁, …, sₙ (in an array or linked list), output a permutation with s_i1 ≤ s_i2 ≤ … ≤ s_in.
- **Objects** can be anything comparable: integers, dates, points, composite keys (last name + first name, city + province).
- **Applications:** databases, data compression, coding, networking, data security, bioinformatics. Sorting is often a step inside other algorithms.

There are two families of sorting algorithms:

| Comparison-based | Index-based |
|---|---|
| Objects are compared with a **Comparator** ("Smith Jack" < "Smith John", 2.0 < 2.05, (3,4) < (3,5)) | Objects (or attributes) are placed in **positions given by an index** |
| Mergesort, quicksort, heapsort, insertion/selection, shellsort | Bucket sort, radix sort, lexicographic sort, counting sort |

Watch out for strings: "14" < "2" as strings, but 2 < 14 as integers.

**Divide and conquer**, the paradigm behind mergesort and quicksort:
1. **Divide** the input S into disjoint subsets S1 and S2.
2. **Recur** on the subproblems.
3. **Conquer**: combine the solutions.

The base case is a subproblem of size 0 or 1.

## 2. Mergesort

```
Algorithm mergeSort(S, C)
  if S.size() > 1 then
    (S1, S2) ← partition(S, n/2)
    mergeSort(S1, C)
    mergeSort(S2, C)
    S ← merge(S1, S2)
```

- **Merge:** compare the fronts of the two sorted sequences and repeatedly move the smaller one to the output. When one side is empty, copy the rest of the other. **O(n)**.
- The merge-sort tree has **height O(log n)**. Each level does O(n) work: at depth i there are 2ⁱ sequences of size n/2ⁱ.
- **O(n log n) in the best, average and worst case.**
- **Stable**. Not in-place: in-place mergesort is complex and impractical.
- Accesses data **sequentially**, so it suits huge data (> 1M), linked lists and external sorting.

Slide example: 7 2 9 4 3 8 6 1 → (7 2 9 4 → 2 4 7 9) + (3 8 6 1 → 1 3 6 8) → **1 2 3 4 6 7 8 9**.

## 3. Quicksort

Quicksort is a **randomized** divide-and-conquer algorithm.
1. **Divide:** pick a random pivot x. Partition S into **L** (< x), **E** (= x) and **G** (> x).
2. **Recur:** sort L and G.
3. **Conquer:** join L, E and G.

### Worst case: O(n²)
This happens when the pivot is always the **unique minimum or maximum**, for example a sorted input with the first or last element as pivot. One of L and G then has size n − 1:

(n − 1) + (n − 2) + … + 1 = **n(n − 1)/2** → **O(n²)**

### Average case: O(n log n)
- A call on s elements is **good** if L and G each have fewer than 3s/4 elements, and **bad** otherwise.
- Half of the possible pivots are good, so **a call is good with probability ½**.
- Probabilistic fact: you expect **2k** coin tosses to get k heads. So at depth i, about i/2 ancestors were good calls, and the input size is at most (3/4)^(i/2) · n.
- So the **expected height is O(log n)** (about 2 log_(4/3) n). Each level does O(n) work, giving **O(n log n) expected**.

### In-place quicksort (the slides' version)
```
Algorithm inPlaceQuickSort(S, a, b)
  if a ≥ b then return
  p ← S[b]                       // pivot = last element
  l ← a; r ← b − 1
  while l ≤ r do
    while l ≤ r and S[l] ≤ p do l ← l + 1
    while l ≤ r and S[r] ≥ p do r ← r − 1
    if l < r then swap S[l] and S[r]
  swap S[l] and S[b]             // put the pivot in its final place
  inPlaceQuickSort(S, a, l − 1)
  inPlaceQuickSort(S, l + 1, b)
```
- Afterwards, elements before l are ≤ the pivot and elements after l are ≥ the pivot.
- For in-place, elements **≤ the pivot go into L** (not just <).
- **O(n log n) average, O(n²) worst.** Dual-pivot quicksort is faster than single-pivot.

Slide trace: `85 24 63 45 17 31 96 50`, pivot 50.
- Swap 85 and 31 → `31 24 63 45 17 85 96 50`
- Swap 63 and 17 → `31 24 17 45 63 85 96 50`
- Put the pivot in place → **`31 24 17 45 50 85 96 63`**

## 4. Heapsort

**PQ-sort:** insert all n items into a priority queue, then removeMin n times.

```
Algorithm PQ-Sort(S, C)
  P ← priority queue with comparator C
  while not S.isEmpty() do
    e ← S.remove(S.first()); P.insertItem(e, e)
  while not P.isEmpty() do
    e ← P.removeMin(); S.insertLast(e)
```

**Heapsort** uses a heap as the priority queue. insert and removeMin are O(log n) each, so the total is **O(n log n)**, using O(n) space.

### In-place heapsort
One array holds both the heap and the sorted sequence.
- **Increasing order:** use a **reverse comparator**, i.e. a max-heap with the largest key at the root.
- **Decreasing order:** keep a min-heap.
- **Phase 1:** move the heap boundary left to right; at step i, add element i to the heap (upheap).
- **Phase 2:** move the boundary right to left; at each step, remove the root and store it at the end of the array (downheap).

Slide example, min-heap on S = 6, 2, 7, 9, 5 (gives decreasing order):

| Step | Array |
|---|---|
| Phase 1 done | 2 5 7 9 6 |
| remove 2 | 5 6 7 9 \| 2 |
| remove 5 | 6 9 7 \| 5 2 |
| remove 6 | 7 9 \| 6 5 2 |
| remove 7 | **9 7 6 5 2** |

## 5. Other comparison sorts

- **Selection sort, insertion sort and bubble sort:** simple but slow, **O(n²)** worst case. Insertion sort is **O(n)** in the best case (already sorted). All three are in-place and suit small data (< 1K).
- **Shellsort:** several passes. Each pass sorts elements i_j positions apart, using a gap sequence i₁, i₂, …, i_k that ends with 1.
  - Hibbard's sequence (1, 3, 7, …, 2ᵏ − 1) gives **O(n^(3/2))** worst case.
  - Other sequences give O(n^(4/3)).
  - "Interesting only for academic purposes."
- In practice, **quicksort and heapsort** are the preferred sorts.

## 6. Summary table

| Algorithm | Worst | Average | Best | Notes (slides) |
|---|---|---|---|---|
| Selection | O(n²) | O(n²) | O(n²) | slow, in-place, small data (< 1K) |
| Insertion | O(n²) | O(n²) | **O(n)** | slow, in-place, small data (< 1K) |
| Shellsort | depends on the sequence (O(n^(4/3))) | | O(n log n) | academic interest only |
| Heapsort | O(n log n) | O(n log n) | O(n log n) | fast, **in-place**, large data (1K–1M) |
| Mergesort | O(n log n) | O(n log n) | O(n log n) | fast, **sequential access**, huge data (> 1M) |
| Quicksort | **O(n²)** | O(n log n) | O(n log n) | fast, **in-place**, large data (1K–1M) |
| Bucket sort | O(n + N) | | | **stable**, keys in [0, N − 1] |
| Radix sort | O(d(n + N)) | | | d-tuples, stable bucket sort per digit |
| Counting sort | O(n + N) | | | integers in [0, N − 1] |

**Stable** means equal keys keep their input order. Mergesort, insertion, bubble, bucket, radix and counting sort can be stable. Quicksort, heapsort, selection sort and shellsort are not.

## 7. Selection

**Problem:** find the k-th smallest key of an unsorted list of n keys.
- **Naive:** sort, then pick the k-th → O(n log n).
- **Heap-based:** build a heap in O(n), then k removeMins → O(n + k log n).
- **Prune-and-search (quickselect):** divide and conquer plus pruning.

```
Algorithm quickSelect(S, k)
  if n = 1 then return S[0]
  pick a random pivot x of S
  split S into L (< x), E (= x), G (> x)
  if k ≤ |L| then return quickSelect(L, k)
  else if k ≤ |L| + |E| then return x
  else return quickSelect(G, k − |L| − |E|)
```
- **O(n) average.** The worst case can also be brought down to O(n) (deterministic selection), but the hidden constants make that slow in practice.
- Randomized quickselect can be done in-place.

### Lower bounds for comparison-based selection

| Find | At least |
|---|---|
| the smallest key | **n − 1** comparisons |
| the two smallest | **n + ⌈log n⌉ − 2** |
| the median | **3n/2 − O(log n)** |
| the k-th smallest | n − k + log C(n, k − 1) |
| the min **and** max | **3n/2 − 2** |

## 8. Bucket sort

S holds n entries (key, element) with keys in **[0, N − 1]**, and B is an array of N buckets (sequences).
1. **Phase 1:** move each entry (k, o) into bucket B[k]. This takes O(n).
2. **Phase 2:** for i = 0 … N − 1, append the contents of B[i] to S. This takes O(n + N).

The total is **O(n + N)**, and bucket sort is **stable**.

Slide example: (7,d) (1,c) (3,a) (7,g) (3,b) (7,e) → **(1,c) (3,a) (3,b) (7,d) (7,g) (7,e)**.

## 9. Radix sort

- A specialisation of **lexicographic sort** that uses **bucket sort as the stable sort for each dimension**.
- Works on d-tuples (or d-digit numbers) where each component is an integer in [0, N − 1].
- It sorts from the **last dimension (least significant digit) to the first**:

```
for i ← d downto 1 do bucketSort(S, N)    // on component i
```

- Time **O(d(n + N))**.
  - If d is constant and N = O(n) → **O(n)**.
  - If d = log n and N = O(n) → O(n log n).

Slide example: 329 457 657 839 436 720 355
- Ones digit → 720 355 436 457 657 329 839
- Tens digit → 720 329 436 839 355 457 657
- Hundreds digit → **329 355 436 457 657 720 839**

These results depend on assumptions about the keys. Comparison sorts assume nothing about the keys.

## 10. Counting sort

A simplification, or special case, of radix sort. It uses **N counters** instead of buckets.

```
Algorithm Counting-sort(S, N)       // integers in [0, N − 1]
  C ← array of N counters (all 0)
  for i ← 0 to n − 1 do C[S[i]] ← C[S[i]] + 1
  i ← 0; j ← 0
  while i < N do
    if C[i] > 0 then S[j] ← i; j ← j + 1; C[i] ← C[i] − 1
    else i ← i + 1
```

- **O(n + N)**, which is O(n) if N = O(n).
- Works on arrays of non-negative integers. Strings and other types must first be converted to integers.

## 11. Lower bound (not in the exam)

The slides mark this as optional. Any comparison sort is a decision tree with n! leaves, so its height is at least log(n!) ≥ (n/2) log(n/2), which is **Ω(n log n)**.

## 12. Sorting in Java

- `Collections.sort` (Java 8) uses **mergesort**. Implementers may change the algorithm, but it must stay **stable**.
- `Arrays.sort` (Java 8) uses **dual-pivot quicksort**.

## 13. The instructor's sample questions

1. **Leaderboard of millions of players with unique scores; list the top ten.** → **Heapsort / heap.** Build a max-heap in O(n), then extract 10 in O(k log n). That is far cheaper than sorting everything.
2. **Hash table where collisions are likely** (Chapter 2) → double hashing.
3. **Real-time stock app, frequently queried stocks** (Chapter 3) → splay tree.

### Choosing a sort (real-world uses)

| Situation | Pick |
|---|---|
| Huge data, external files, linked lists, stability needed | **Mergesort** |
| General in-memory arrays, fastest on average | **Quicksort** (random or dual pivot) |
| Guaranteed O(n log n) with O(1) extra memory (embedded systems), top-k | **Heapsort** |
| Tiny or nearly sorted arrays | **Insertion sort** |
| Integers in a small range (grades 0–100, ages) | **Counting / bucket sort** |
| Fixed-length numbers or strings (IDs, postal codes, dates) | **Radix sort** |
| The k-th smallest or the median without sorting | **Quickselect** |

## 14. Last-minute checklist

- [ ] Divide, recur, conquer; mergesort and its merge procedure; O(n log n) always; stable
- [ ] Quicksort L/E/G; worst case n(n − 1)/2 on a min or max pivot; good calls have probability ½; expected O(n log n)
- [ ] Trace the slides' in-place quicksort (l moves right past ≤ p, r moves left past ≥ p, swap, then place the pivot)
- [ ] Heapsort phases; increasing order uses a max-heap (reverse comparator)
- [ ] Summary table from memory, including which sorts are in-place, which are stable, and the data sizes
- [ ] Quickselect O(n) average; the selection lower bounds
- [ ] Bucket O(n + N) and stable; radix from the least significant digit, O(d(n + N)); counting O(n + N)
- [ ] Java: Collections.sort is mergesort, Arrays.sort is dual-pivot quicksort
