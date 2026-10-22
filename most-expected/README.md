# Most Expected: Mid-Term I (Friday 23 October 2026)

COMP 8547, Chapters 1–4. **14:30–17:30 (2 hours of writing), closed book, bring pens.** ER 3119, ER 3120, LT 3107.

This page is the night-before list: the questions most likely to appear, with short answers. It is based on:
- the exam info page and its four sample questions
- the three "Sample Mid-Term Questions" at the end of the Chapter 4 slides
- the end-of-chapter exercises the instructor points to (e.g. "Ch 3 Ex 19: insert 5 and delete 8 in a red-black tree")

| Section | Count | What to expect |
|---|---|---|
| MCQ Level I | 10 | definitions and facts, like "What does Big-O represent?" |
| MCQ Level II | 10 | scenarios: "which structure or algorithm is best here?" |
| Short answer Level I | 10 | fill in a complexity or a fact, no explanation |
| Short answer Level II | 5 | **hands-on**: red-black / AVL / splay insert and delete, finding c and n0, hashing tables, sorting traces |

**★★★** = almost certain · **★★** = likely · **★** = possible

---

## 1. The five Level II hands-on questions (biggest marks)

### ★★★ Red-black tree: insert X, delete Y, write the in-order traversal as KEY(B/R)
The exam page's own example. Tree: `9B[4R[2B,6B[-,7R]],15B[12R,21R]]`. Insert 5, delete 15:
**2(B) − 4(R) − 5(R) − 6(B) − 7(R) − 9(B) − 12(R) − 21(B)**

Rules to apply:
- **Insert:** the new node is **red**. If its parent is black, you are done.
  - Double red with a **black uncle** → **restructure**: the middle key becomes black, the other two red. Done.
  - Double red with a **red uncle** → **recolour**: parent and uncle black, grandparent red (the root stays black). The double red may move up; repeat.
- **Delete:** two children → copy the **inorder successor** into the node, then delete the successor. If the removed node or its replacement is red, colour the replacement black. Done. Otherwise the replacement is **double black**; look at its sibling y:
  - **Case 1**, y black with a red child → **restructure**. The middle takes the old parent's colour; the other two become black.
  - **Case 2**, y black with black children → **recolour** y red. A red parent becomes black (done); a black parent becomes double black (move up).
  - **Case 3**, y red → **rotate** y up and swap the colours of y and the parent, then apply Case 1 or 2.
- **Before writing the answer, check:** the root is black, there is no red-red pair, and every path has the same number of blacks.

Other likely versions on the same tree: insert 8 → `… 6(R) − 7(B) − 8(R) …` (restructure). Insert 13 → 12 and 21 black, 15 red (recolour). Delete 2 → 6 moves up as red with 4 and 7 black (Case 1).

### ★★★ Find the upper bound (c and n0)
"Find upper bound for f(n) = 2n + 10." 2n + 10 ≤ cn ⇒ (c − 2)n ≥ 10 ⇒ **c = 3, n0 = 10**, so f(n) is **O(n)**.
- Quick method for any polynomial: replace every term by its coefficient times the top power. For example, 3n² + 5n + 2 ≤ 10n² for n ≥ 1 → **c = 10, n0 = 1**.
- Always **write c and n0 explicitly** and show the inequality.

### ★★★ AVL tree: insert or delete and rebalance
- At the first unbalanced node z (heights differ by more than 1), take **y = the child** and **x = the grandchild** on the path.
- Same direction (left-left or right-right) → **single rotation**. Zig-zag (left-right or right-left) → **double rotation**. The middle key of x, y, z becomes the subtree root.
- **Insert:** one fix is enough. **Delete:** use the *taller* child each time and keep checking up to the root.
- Slide example: insert 54 into `44[17[-,32],78[50[48,62],88]]` → `44[17[-,32],62[50[48,54],78[-,88]]]`.
- Classic: insert 10, 20, 30, 40, 50, 25 → `30[20[10,25],40[-,50]]`.

### ★★ Splay tree: insert or search, then splay
- **zig:** the parent is the root. **zig-zig:** same direction twice; rotate the grandparent first. **zig-zag:** different directions; rotate x twice.
- Splay **the found node** on search, **the new node** on insert, and **the parent of the removed node** on delete.
- Slide example: insert 5 into `6[2[1,4],9[8,-]]` → zig-zig, then zig → `5[4[2[1,-],-],6[-,9[8,-]]]`.

### ★★ Hashing: fill the table (N = 13, h(k) = k mod 13)
Keys 18, 41, 22, 44, 59, 32, 31, 73:
- **Linear probing** `[–, –, 41, –, –, 18, 44, 59, 32, 22, 31, 73, –]`
- **Double hashing**, d2(k) = 7 − (k mod 7): `[31, –, 41, –, –, 18, 32, 59, 73, 22, 44, –, –]` (31 probes 5, 9, 0)
- **Quadratic probing** tries i + 1, i + 4, i + 9, … mod N.

### ★★ Sorting traces
- **In-place quicksort** (pivot = last element): `85 24 63 45 17 31 96 50` → after the first partition **`31 24 17 45 50 85 96 63`**.
- **Heap insert/removeMin** in array form: children at 2i and 2i + 1, parent at ⌊i/2⌋. Inserting 15, 9, 20, 4, 11, 2, 7 gives `[2, 9, 4, 15, 11, 20, 7]`.
- **Radix sort:** least significant digit first, using a stable sort each pass.

---

## 2. Scenario questions (MCQ Level II) and their answers

The instructor's own three samples will appear in some form. Give the reason, not just the name.

| ★ | Scenario | Answer | Why |
|---|---|---|---|
| ★★★ | Leaderboard of **millions**, list the **top 10** | **Heap / heapsort** | build in O(n) + 10 × removeMax at O(k log n), no full sort |
| ★★★ | Hash table with **many collisions**; avoid clustering | **Double hashing** | each key gets its own step d2(k), so there is no primary or secondary clustering |
| ★★★ | Stock app with **frequently queried** items, fast search and update | **Splay tree** | hot keys stay near the root (pick red-black if the question stresses a *guaranteed* worst case) |
| ★★ | Data **bigger than memory**, a linked list, or stability needed | **Mergesort** | sequential access, stable, O(n log n) always |
| ★★ | Little memory, **guaranteed** O(n log n) | **Heapsort** | in-place, O(n log n) worst case |
| ★★ | Fastest general in-memory sort | **Quicksort** (random or dual pivot) | O(n log n) average, in-place; Java's `Arrays.sort` |
| ★★ | Small or **nearly sorted** list | **Insertion sort** | O(n) best case |
| ★★ | Integers in a **small range** (marks 0–100) | **Counting / bucket sort** | O(n + N) |
| ★★ | Fixed-length numbers (IDs, phone numbers) | **Radix sort** | O(d(n + N)) ≈ O(n) |
| ★★ | k-th smallest or median, once | **Quickselect** | O(n) average |
| ★★ | Fast lookup by key, **no order** needed | **Hash table** | O(1) expected |
| ★★ | Lookups **plus order and range queries** | **Balanced BST (red-black / AVL)** | O(log n) worst case, inorder = sorted |
| ★ | Read-heavy, rarely updated | **AVL** | stricter balance, so a lower tree |
| ★ | Update-heavy | **Red-black** | fewer rotations; Java TreeMap |
| ★ | Always run the highest-priority job | **Heap / priority queue** | O(log n) insert and removeMin |
| ★ | Count word frequencies | **Hash table** keyed by word | the slides' application |
| ★ | Sorted input to quicksort with a last-element pivot | **O(n²)** | the pivot is always the max; fix it with a random pivot |

---

## 3. Facts most likely in MCQ Level I and short answer Level I

### Chapter 1 ★★★
- **Big-O = upper bound = rate of growth** of running time as n grows (the exam's sample MCQ). The slides pair **O ↔ worst, Ω ↔ best, Θ ↔ average**.
- Growth order: **1 < log n < n < n log n < n² < n³ < 2ⁿ**.
- O(f) + O(g) = O(max(f, g)). Use the simplest, smallest class.
- f is O(g) and Ω(g) ⇔ Θ(g). For o and ω the inequality holds for **every** c; for O and Ω for **some** c.
- Loops: halving or doubling → **O(log n)**. Nested → multiply. Sequential → add. Two independent loops → **O(N + M)**. A `break` on the first pass → constant.
- arrayMax **8n − 3**. Linear search **O(n)**. Binary search **T(n) = T(n/2) + 1 = O(log n)**.
- Prefix averages: quadratic **O(n²)** vs running sum **O(n)**.
- MCSS: cubic O(n³), quadratic O(n²), divide and conquer **O(n log n)** (T(n) = 2T(n/2) + n), linear **O(n)**. All negative → **0**. The sequence −3, 10, −2, 11, −5, −2, 3 → **19**.

### Chapter 2 ★★★
- Collisions: **separate chaining** (Java HashMap), **linear probing** (primary clustering), **quadratic probing** (secondary clustering, may not find an empty cell), **double hashing** (d2 = q − k mod q, q < N, both prime, never 0).
- **Load factor α = n/N**, keep it **< 0.5**. Expected O(1). Rehash when it gets too high.
- Java HashMap: capacity **16**, load factor **0.75**.
- Cuckoo hashing uses two tables and displaces occupants. Extendible hashing serves disk data in at most 2 disk accesses. Perfect hashing gives worst-case O(1).
- Heap: heap order + complete tree. **Height O(log n)**. Insert (upheap) and removeMin (downheap) are **O(log n)**. **Bottom-up build O(n).**
- Selection with a heap: **O(n + k log n)**.
- d-heap height O(log_d n). Fibonacci heap removeMin is O(log n) amortized; other operations O(1) amortized.
- Java `PriorityQueue`: `add`, `poll`.

### Chapter 3 ★★★
- **Worst-case BST search is O(n)** (the exam's sample short answer). Average O(log n).
- **Inorder of a BST = sorted.** Postorder evaluates an expression tree.
- Proper binary tree: **e = i + 1**, n = 2e − 1.
- AVL: heights differ by ≤ 1, O(log n) everything; insert needs one restructure.
- (2,4) tree: ≤ 4 children, all leaves at the same depth.
- Red-black: root black, leaves black, no red-red, equal black depth. Height ≤ 2 × the (2,4) height = O(log n). **Java TreeMap and TreeSet are red-black.**
- Splay: no stored info; **O(log n) average, O(n) worst**.
- wavl trees: **not in the exam**.

### Chapter 4 ★★★

| Sort | Worst | Average | Best | Notes |
|---|---|---|---|---|
| Selection | n² | n² | n² | in-place |
| Insertion | n² | n² | **n** | in-place, stable |
| Heapsort | n log n | n log n | n log n | **in-place** |
| Mergesort | n log n | n log n | n log n | **stable**, not in-place |
| Quicksort | **n²** | n log n | n log n | in-place |
| Bucket / counting | n + N | | | stable |
| Radix | d(n + N) | | | |

- Quicksort worst-case comparisons are **n(n − 1)/2**. A "good" pivot has probability **½**.
- Quickselect **O(n)** average.
- Lower bounds: min **n − 1**; two smallest **n + ⌈log n⌉ − 2**; min and max **3n/2 − 2**.
- Java: `Collections.sort` = mergesort (stable); `Arrays.sort` = dual-pivot quicksort.
- The Ω(n log n) sorting lower bound is **not in the exam**.

---

## 4. Ten-minute warm-up before the exam

1. Write the four red-black properties and the three delete cases from memory.
2. Redo the exam's red-black example (insert 5, delete 15) without looking.
3. Find c and n0 for 2n + 10 and for 3n² + 5n + 2.
4. Write the sorting table above from memory.
5. Say the three instructor scenarios out loud: **heap, double hashing, splay tree**.

**In the exam:** use the draft paper and redraw the tree after every step. Write in-order answers in the exact format they ask for (`KEY(B) − KEY(R) − …`). For c and n0, always state both numbers.

More practice: [chapter question banks](../chapter-1/questions.md) · [Chapter 4 justify questions](../chapter-4/justify-questions.md) · [full practice set](../practice-questions.md). Good luck!
