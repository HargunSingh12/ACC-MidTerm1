# COMP 8547 Mid-Term I: Practice Questions

Same format as the real exam: MCQ Level I, MCQ Level II (scenarios), short answer Level I, short answer Level II (hands-on). The answer key is at the bottom. Try each section before looking.

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

---
---

# Answer key

## Part A
A1 c · A2 b · A3 b · A4 c · A5 b · A6 c · A7 c · A8 d · A9 c · A10 b · A11 c (that is the AVL property) · A12 b · A13 c · A14 b · A15 b

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

## Part C
C1 O(n) · C2 O(1) · C3 O(log n) · C4 O(n log n) · C5 8 (e = i + 1) · C6 0.5 · C7 O(d(n + N)) · C8 zig, zig-zig, zig-zag · C9 4 · C10 O(log n) · C11 O(n) · C12 O(n) · C13 n − 1 · C14 3n/2 − 2 · C15 O(n + k log n) · C16 0.75 · C17 O(n) · C18 T(n/2) + 1 (→ O(log n)) · C19 one (one trinode restructure) · C20 O(log n), exactly ⌊log₂ n⌋

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
