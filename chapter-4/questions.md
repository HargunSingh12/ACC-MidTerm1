# Chapter 4: Sorting, Question Bank

Every question type from the Mid-Term I format, for **Chapter 4 only** (mergesort, quicksort, heapsort, other comparison sorts, selection, bucket, radix and counting sort). The answer key is at the bottom. Notes are in [README.md](README.md).

| Part | Exam section | Questions |
|---|---|---|
| A | MCQ Level I (simple) | A1–A18 |
| B | MCQ Level II (scenarios) | B1–B14 |
| C | Short answer Level I (fill in) | C1–C20 |
| D | Short answer Level II (hands-on) | D1–D22 |

---

## Part A. MCQ Level I

**A1.** The three steps of divide and conquer are: (a) split, sort, search (b) divide, recur, conquer (c) partition, pivot, merge (d) insert, remove, sort

**A2.** Merging two sorted sequences with n/2 elements each takes: (a) O(log n) (b) O(n) (c) O(n log n) (d) O(n²)

**A3.** The height of the merge-sort tree is: (a) O(1) (b) O(log n) (c) O(n) (d) O(n log n)

**A4.** Quicksort's worst case happens when the pivot is always: (a) the median (b) a random element (c) the unique minimum or maximum (d) the middle index

**A5.** In the average-case analysis of quicksort, a call is "good" with probability: (a) 1/4 (b) 1/2 (c) 3/4 (d) 1

**A6.** In the slides' in-place quicksort, the pivot is: (a) the first element (b) the last element (c) the median of three (d) a random element

**A7.** To sort in **increasing** order with in-place heapsort you use: (a) a min-heap (b) a max-heap / reverse comparator (c) a hash table (d) a BST

**A8.** Which sort has a best case of O(n)? (a) selection sort (b) insertion sort (c) heapsort (d) mergesort

**A9.** Shellsort with Hibbard's sequence has worst case: (a) O(n) (b) O(n log n) (c) O(n^(3/2)) (d) O(n³)

**A10.** In practice, the slides say the preferred sorting algorithms are: (a) bubble and selection (b) quicksort and heapsort (c) shellsort and insertion (d) radix and bucket

**A11.** Which sort is recommended for **huge** data (> 1M) because it accesses data sequentially? (a) selection (b) quicksort (c) mergesort (d) heapsort

**A12.** Quickselect's average running time is: (a) O(log n) (b) O(n) (c) O(n log n) (d) O(n²)

**A13.** The minimum number of comparisons to find the smallest of n keys is: (a) log n (b) n − 1 (c) n (d) 3n/2

**A14.** Bucket sort runs in: (a) O(n log n) (b) O(n + N) (c) O(N log n) (d) O(n²)

**A15.** A sort is **stable** if: (a) it never uses extra memory (b) equal keys keep their relative order (c) it is always O(n log n) (d) it never swaps

**A16.** Radix sort processes the digits: (a) from most to least significant (b) from least to most significant (c) in random order (d) only the first digit

**A17.** Counting sort uses: (a) buckets of linked lists (b) N counters (c) a heap (d) comparisons

**A18.** Java's `Arrays.sort` (for primitives) and `Collections.sort` use, respectively: (a) mergesort and quicksort (b) dual-pivot quicksort and mergesort (c) heapsort and radix (d) insertion and shellsort

---

## Part B. MCQ Level II (scenarios)

**B1.** A competition leaderboard has millions of participants with unique scores; you must list the **top ten**. Most efficient? (a) mergesort (b) quicksort (c) heap sort / heap (d) counting sort *(instructor's sample question)*

**B2.** Sort 100 GB of records with 8 GB of RAM. Choose: (a) quicksort (b) heapsort (c) mergesort (d) insertion sort

**B3.** An embedded device needs guaranteed O(n log n) and almost no extra memory. Choose: (a) mergesort (b) quicksort (c) heapsort (d) counting sort

**B4.** Sort 300,000 exam marks, each an integer from 0 to 100. Choose: (a) counting sort (b) quicksort (c) mergesort (d) shellsort

**B5.** Sort 2 million 10-digit phone numbers as fast as possible. Choose: (a) counting sort over all 10¹⁰ values (b) radix sort by digit (c) bubble sort (d) selection sort

**B6.** Records are already sorted by name. You re-sort by city and need names to stay in order within each city. You need a: (a) stable sort such as mergesort (b) quicksort (c) heapsort (d) selection sort

**B7.** Sort a small list of 25 items that is almost sorted. Choose: (a) insertion sort (b) heapsort (c) radix sort (d) mergesort

**B8.** A general-purpose library must sort large in-memory arrays fastest on average. Choose: (a) bubble sort (b) quicksort with a random or dual pivot (c) selection sort (d) shellsort

**B9.** Quicksort with the last element as pivot is given an already-sorted array of 1 million items. What happens? (a) O(n), very fast (b) O(n log n) (c) O(n²), very slow (d) it fails

**B10.** You need the **median** of 50 million unsorted values once. Choose: (a) sort with mergesort (b) quickselect (c) build an AVL tree (d) insertion sort

**B11.** Sort a singly linked list of 3 million nodes. Choose: (a) mergesort (b) in-place quicksort (c) heapsort (d) shellsort

**B12.** You need both the minimum and maximum of n sensor readings with the fewest comparisons. About how many? (a) 2n − 2 (b) 3n/2 − 2 (c) n log n (d) n/2

**B13.** Sort student records by (year, then month, then day) of birth. Which approach? (a) radix/lexicographic sort with a stable bucket sort per field, starting with day (b) one quicksort on the day field only (c) heapsort on the year only (d) counting sort on the year only

**B14.** Your data is integers in the range [0, n²]. Counting sort would take: (a) O(n) (b) O(n²) (c) O(log n) (d) O(1)

---

## Part C. Short answer Level I

C1. Base case of mergesort's recursion: subproblems of size ______.
C2. Total running time of mergesort: ______ (best, average and worst).
C3. Number of comparisons quicksort makes in the worst case: ______.
C4. Expected height of the quicksort recursion tree: ______.
C5. Average and worst-case times of in-place quicksort: ______ and ______.
C6. In in-place quicksort, elements ______ the pivot are placed in L.
C7. Running time of heapsort: ______.
C8. Space used by heapsort (PQ-sort on a heap): ______.
C9. Worst-case running time of selection, insertion and bubble sort: ______.
C10. Running time of quickselect: ______ average.
C11. Lower bound for finding the two smallest keys: ______ comparisons.
C12. Lower bound for finding the median: ______ comparisons.
C13. Lower bound for finding both the min and the max: ______ comparisons.
C14. Bucket sort phase 1 takes ______; phase 2 takes ______.
C15. Radix sort on d-tuples with components in [0, N − 1]: ______.
C16. If d is constant and N = O(n), radix sort runs in ______.
C17. Counting sort running time: ______.
C18. Lower bound for comparison-based sorting (not in the exam): ______.
C19. Data-size guidance in the slides: heapsort and quicksort for ______, mergesort for ______.
C20. Collections.sort must use a ______ sorting method.

---

## Part D. Short answer Level II (hands-on)

**D1.** (Slide example) Mergesort 7 2 9 4 3 8 6 1. Show every merge.

**D2.** Merge A = 12 19 24 42 62 with B = 18 40 56 61. Show the output and count the comparisons.

**D3.** Quicksort (L/E/G version, **first element as pivot**) on 7 2 9 4 3 7 6 1. Show every call with L, E and G.

**D4.** (Slide example) In-place quicksort (slides' version, pivot = last) on 85 24 63 45 17 31 96 50. Show the first partition step by step.

**D5.** In-place quicksort (slides' version) on 30 80 10 60 20 90 50 40. List every partition call: the range, the pivot and the array after it.

**D6.** In-place quicksort (slides' version) on 3 8 2 5 1 4 7 6. Give the array after the first partition and the pivot's final index.

**D7.** (Slide example) In-place heapsort with a **min-heap** on S = 6, 2, 7, 9, 5. Show the array after phase 1 and after each removal. Which order do you get?

**D8.** In-place heapsort with a **max-heap** (increasing order) on 5, 3, 8, 1, 4. Show the array after phase 1 and after each removal.

**D9.** Insertion sort 5 2 4 6 1 3. Show the array after each pass.

**D10.** Selection sort 5 2 4 6 1 3. Show the array after each pass.

**D11.** Bubble sort 5 2 4 6 1 3. Show the array after each pass.

**D12.** Shellsort 35 33 42 10 14 19 27 44 with gaps 3, then 1 (insertion sort within each gap). Show the array after each gap.

**D13.** Quickselect the 5th smallest of 15 7 22 3 9 30 11 5, always using the first element as pivot. Show each call.

**D14.** For n = 8, 10 and 100, give the lower bounds on comparisons for: the minimum, the two smallest, and both the min and max.

**D15.** Bucket sort the entries (4,a) (2,b) (4,c) (0,d) (2,e) (1,f) with keys in [0, 4]. Give the output and say which property it shows.

**D16.** (Slide example) Radix sort 329 457 657 839 436 720 355. Show each pass.

**D17.** Radix sort 53 89 150 36 633 233 7 (3 digits). Show each pass.

**D18.** Counting sort 3 6 4 1 3 4 1 4 with keys in [0, 6]. Give the counter array and the output.

**D19.** Lexicographic sort of the pairs (2,1) (1,3) (2,0) (1,1) (0,2) using a stable sort on the second component first, then on the first. Show both passes.

**D20.** Give 8 integers that are a worst-case input for the slides' in-place quicksort. How many comparisons does it make? Do mergesort and heapsort slow down on it?

**D21.** What are the running times of mergesort, quicksort and heapsort when all n elements are equal? And of radix and counting sort when all n numbers are in [1, n] and equal?

**D22.** 25 keys in [0, 2³² − 1]. Give the asymptotic running times of counting sort (one counter per value), radix sort (base 2¹⁶, so d = 2), and quicksort, mergesort and heapsort.

---
---

# Answer key

## Part A
A1 b · A2 b · A3 b · A4 c · A5 b · A6 b · A7 b · A8 b · A9 c · A10 b · A11 c · A12 b · A13 b · A14 b · A15 b · A16 b · A17 b · A18 b

## Part B
- B1 **c**: build a max-heap in O(n), then extract 10 in O(k log n). Much cheaper than sorting everything.
- B2 **c**: mergesort accesses data sequentially, so it suits external sorting.
- B3 **c**: heapsort is in-place and O(n log n) in every case.
- B4 **a**: N = 101, so O(n + N) = O(n).
- B5 **b**: d = 10 digits, N = 10 per digit, so O(d(n + N)) = O(n).
- B6 **a**: stability keeps the earlier name order.
- B7 **a**: insertion sort is O(n) on nearly sorted input and good for small n.
- B8 **b**: quicksort is fastest on average, and a random or dual pivot avoids the bad case.
- B9 **c**: each pivot is the maximum, so it does n(n − 1)/2 comparisons.
- B10 **b**: O(n) average.
- B11 **a**: mergesort needs no random access.
- B12 **b**: 3n/2 − 2, by comparing elements in pairs.
- B13 **a**: least significant field first, with a stable sort each pass.
- B14 **b**: N = n², so O(n + N) = O(n²). Radix sort with base n would be O(n).

## Part C
C1 0 or 1 · C2 O(n log n) · C3 n(n − 1)/2 · C4 O(log n) · C5 O(n log n); O(n²) · C6 ≤ (less than or equal to) · C7 O(n log n) · C8 O(n) · C9 O(n²) · C10 O(n) · C11 n + ⌈log n⌉ − 2 · C12 3n/2 − O(log n) · C13 3n/2 − 2 · C14 O(n); O(n + N) · C15 O(d(n + N)) · C16 O(n) · C17 O(n + N) · C18 Ω(n log n) · C19 large data (1K–1M); huge data (> 1M) · C20 stable

## Part D

**D1.**
- 7 | 2 → 2 7 · 9 | 4 → 4 9 · 2 7 | 4 9 → 2 4 7 9
- 3 | 8 → 3 8 · 6 | 1 → 1 6 · 3 8 | 1 6 → 1 3 6 8
- 2 4 7 9 | 1 3 6 8 → **1 2 3 4 6 7 8 9**

**D2.** Comparisons: 12 vs 18, 19 vs 18, 19 vs 40, 24 vs 40, 42 vs 40, 42 vs 56, 62 vs 56, 62 vs 61. B is then empty, so copy 62.
Output **12 18 19 24 40 42 56 61 62**, **8 comparisons**.

**D3.**
- pivot 7: L = 2 4 3 6 1, E = 7 7, G = 9
- on 2 4 3 6 1, pivot 2: L = 1, E = 2, G = 4 3 6
- on 4 3 6, pivot 4: L = 3, E = 4, G = 6

Result **1 2 3 4 6 7 7 9**.

**D4.** Pivot 50, l = 0, r = 6.
- l stops at 85 (index 0); r skips 96 and stops at 31 (index 5) → swap → `31 24 63 45 17 85 96 50`
- l moves to 63 (index 2); r moves to 17 (index 4) → swap → `31 24 17 45 63 85 96 50`
- l moves to 63 (index 4); r moves to index 3; now l > r
- swap S[4] with the pivot → **`31 24 17 45 50 85 96 63`**. Pivot at index 4.

**D5.**
1. [0..7] pivot 40 → `30 20 10 40 80 90 50 60`
2. [0..2] pivot 10 → `10 20 30 …`
3. [1..2] pivot 30 → `10 20 30 …`
4. [4..7] pivot 60 → `… 40 50 60 80 90`
5. [6..7] pivot 90 → `… 80 90`

Sorted **10 20 30 40 50 60 80 90**.

**D6.** Pivot 6: swap 8 and 4 → `3 4 2 5 1 8 7 6`; l stops at 8 (index 5); swap with the pivot → **`3 4 2 5 1 6 7 8`**, pivot at **index 5**.

**D7.**
- Phase 1, inserting one by one: [6] → [2, 6] → [2, 6, 7] → [2, 6, 7, 9] → 5 upheaps → **[2, 5, 7, 9, 6]**
- Phase 2:

| Step | Array |
|---|---|
| remove 2 | 5 6 7 9 \| 2 |
| remove 5 | 6 9 7 \| 5 2 |
| remove 6 | 7 9 \| 6 5 2 |
| remove 7 | 9 \| 7 6 5 2 |

Result **9 7 6 5 2**: a min-heap gives **decreasing** order.

**D8.**
- Phase 1: [5] → [5, 3] → 8 upheaps → [8, 3, 5] → [8, 3, 5, 1] → 4 swaps with 3 → **[8, 4, 5, 1, 3]**
- Phase 2:

| Step | Array |
|---|---|
| remove 8 | 5 4 3 1 \| 8 |
| remove 5 | 4 1 3 \| 5 8 |
| remove 4 | 3 1 \| 4 5 8 |
| remove 3 | 1 \| 3 4 5 8 |

Result **1 3 4 5 8**.

**D9.**

| Pass | Array |
|---|---|
| 1 | 2 5 4 6 1 3 |
| 2 | 2 4 5 6 1 3 |
| 3 | 2 4 5 6 1 3 |
| 4 | 1 2 4 5 6 3 |
| 5 | **1 2 3 4 5 6** |

**D10.**

| Pass | Array |
|---|---|
| 1 | 1 2 4 6 5 3 |
| 2 | 1 2 4 6 5 3 |
| 3 | 1 2 3 6 5 4 |
| 4 | 1 2 3 4 5 6 |
| 5 | **1 2 3 4 5 6** |

**D11.**

| Pass | Array |
|---|---|
| 1 | 2 4 5 1 3 6 |
| 2 | 2 4 1 3 5 6 |
| 3 | 2 1 3 4 5 6 |
| 4 | 1 2 3 4 5 6 |
| 5 | **1 2 3 4 5 6** |

The largest remaining element "bubbles" to the end in each pass.

**D12.** Gap 3 → `10 14 19 27 33 42 35 44`. Gap 1 → **`10 14 19 27 33 35 42 44`**.

**D13.**
- quickSelect(S, 5), pivot 15: |L| = 5 (7 3 9 11 5), |E| = 1, |G| = 2. Since k = 5 ≤ |L|, recurse on L.
- quickSelect(7 3 9 11 5, 5), pivot 7: |L| = 2, |E| = 1. Since k = 5 > 3, recurse on G = 9 11 with k = 5 − 3 = 2.
- quickSelect(9 11, 2), pivot 9: |L| = 0, |E| = 1. Since k = 2 > 1, recurse on G = 11 with k = 1.
- quickSelect(11, 1) → **11**.

Check: the sorted list is 3 5 7 9 **11** 15 22 30.

**D14.**

| n | min (n − 1) | two smallest (n + ⌈log n⌉ − 2) | min & max (3n/2 − 2) |
|---|---|---|---|
| 8 | 7 | 9 | 10 |
| 10 | 9 | 12 | 13 |
| 100 | 99 | 105 | 148 |

**D15.** **(0,d) (1,f) (2,b) (2,e) (4,a) (4,c)**. Equal keys keep their input order (b before e, a before c), so bucket sort is **stable**.

**D16.**
- Ones: 720 355 436 457 657 329 839
- Tens: 720 329 436 839 355 457 657
- Hundreds: **329 355 436 457 657 720 839**

**D17.**
- Ones: 150 53 633 233 36 7 89
- Tens: 7 633 233 36 150 53 89
- Hundreds: **7 36 53 89 150 233 633**

**D18.** C = [0, 2, 0, 2, 3, 0, 1] for keys 0–6. Output **1 1 3 3 4 4 4 6**.

**D19.**
- Pass 1, by the second component: (2,0) (2,1) (1,1) (0,2) (1,3)
- Pass 2, by the first component (stable): **(0,2) (1,1) (1,3) (2,0) (2,1)**

**D20.** Already sorted (or reverse sorted) input, e.g. **1 2 3 4 5 6 7 8**. Every pivot is the max (or min), so it makes 7 + 6 + … + 1 = **28** comparisons → O(n²). Mergesort and heapsort stay **O(n log n)**.

**D21.**
- Mergesort: **O(n log n)**.
- Quicksort: the slides' in-place version puts every element ≤ pivot on the left, so the split is n − 1 / 0 → **O(n²)**. The L/E/G version puts everything in E → **O(n)**.
- Heapsort: upheap and downheap stop immediately → **O(n)**.
- Counting sort: O(n + N) = **O(n)**. Radix sort with d digits: O(d(n + N)) = **O(n)** for constant d.

**D22.** With n = 25 and N = 2³²:
- Counting sort: O(n + N) ≈ **O(2³²)**, dominated by the counters.
- Radix sort with base 2¹⁶ (d = 2): O(2(25 + 65,536)) ≈ **O(2¹⁶)**.
- Quicksort (average), mergesort and heapsort: **O(n log n)**, about 25 · 5 ≈ 116 comparisons. These win easily here.
