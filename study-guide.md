# COMP 8547 Mid-Term I: Study Guide

**Exam:** Friday 23 October 2026, 14:30 to 17:30 (2 h writing + 30 min admin). Rooms ER 3119, ER 3120, LT 3107. Closed book, bring pens.
**Covers:** Chapters 1 to 4 only (no labs or assignments). 100 points.

| Section | Count | What it looks like |
|---|---|---|
| MCQ Level I | 10 | Definitions and facts ("What does Big-O represent?") |
| MCQ Level II | 10 | Scenarios: pick the best structure or algorithm ("top 10 of millions" → heap) |
| Short answer Level I | 10 | Fill in a fact, no explanation ("Worst-case BST access is ___" → O(n)) |
| Short answer Level II | 5 | Hands-on: insert/delete in red-black, AVL, splay trees; find c and n0 for Big-O; etc. Draft paper given |

The instructor says: *research the practical applications of every algorithm and data structure.* Section 6 covers that.

Practice questions with a full answer key are in [practice-questions.md](practice-questions.md).

---

## 1. Algorithm analysis (Ch 1)

**Algorithm:** a finite sequence of unambiguous steps. Properties: correctness, performance (time/space), termination.

**Experimental vs theoretical analysis.** Experimental depends on hardware and language and needs an implementation. Theoretical uses pseudocode, counts primitive operations, covers all inputs, and is machine independent.

**Primitive operations** (constant time in the RAM model): evaluating an expression, assignment, array indexing, calling a method, returning.
- `arrayMax`: T(n) = 8n − 3 → O(n)
- Linear search worst case: T(n) = 3n + 4 → O(n)
- Binary search: T(n) = T(n/2) + 1 → O(log n)

**Growth rates, slowest to fastest:** 1 < log n < n < n log n < n² < n³ < 2ⁿ.
Drop lower-order terms and constants: n⁴ + 2n² + 100n + 500 ≈ n⁴. On a log-log chart the slope is the growth rate (except exponential).

**Cases:** worst (largest time over all inputs), best (fastest input), average (expected value over all inputs).

### Asymptotic notation

| Notation | Meaning | Definition |
|---|---|---|
| O(g) | upper bound | ∃ c > 0, n0 ≥ 1: f(n) ≤ c·g(n) for all n ≥ n0 |
| Ω(g) | lower bound | ∃ c > 0, n0: f(n) ≥ c·g(n) for n ≥ n0 |
| Θ(g) | tight bound | ∃ c′, c″ > 0, n0: c′g(n) ≤ f(n) ≤ c″g(n) |
| o(g) | loose upper | for **every** c > 0 there is n0 with f(n) < c·g(n) |
| ω(g) | loose lower | for **every** c > 0 there is n0 with f(n) > c·g(n) |

- The slides also pair them with cases: **O ↔ worst case, Ω ↔ best case, Θ ↔ average case**. Expect an MCQ worded this way.
- f is O(g) and Ω(g) ⇔ f is Θ(g). f is o(g) ⇔ g is ω(f).
- 3n² − 2n + 1 is o(n³) but not o(n²); it is ω(n) but not ω(n²).
- Rules: polynomial of degree d is O(nᵈ); use the simplest, smallest class (2n is O(n), not O(n²)); O(f) + O(g) = O(max(f, g)).

**Finding c and n0 (Level II favourite).** f(n) = 2n + 10 is O(n): 2n + 10 ≤ cn ⇒ (c − 2)n ≥ 10 ⇒ pick **c = 3, n0 = 10**. Any valid pair works; show the inequality.

### Loop rules
1. Single loop: body × iterations → O(n).
2. Nested loops: multiply sizes → O(n²).
3. Consecutive statements: add, keep the largest.
4. If/else: test + the larger branch.
5. Halving or doubling the counter (`i *= 2`, `i /= 2`) → O(log n).
- Two independent loops of N and M → **O(N + M)**.
- `break` in the inner loop on its first pass makes it O(1) → whole thing O(n).
- Slide examples: n/2 × n/2 × log n → **O(n² log n)**; n/2 × log n × log n → **O(n log² n)**.

### Case studies
| Problem | Algorithms | Time |
|---|---|---|
| Search sorted array | linear / binary | O(n) / O(log n) |
| Prefix averages | quadratic / running sum | O(n²) / O(n) |
| MCSS (max contiguous subsequence sum) | cubic / quadratic / divide and conquer / linear | O(n³) / O(n²) / O(n log n) with T(n) = 2T(n/2) + n / O(n) |

MCSS conventions: if all numbers are negative, MCSS = 0. Example: −3, 10, −2, 11, −5, −2, 3 → **19**. The linear algorithm keeps a running sum and resets it to 0 when it goes negative; it finds the value, not the subsequence.

---

## 2. Maps, hashing, priority queues, heaps (Ch 2)

**ADT:** a set of objects plus operations (data, operations, error conditions).
**Map ADT:** get(k), put(k, v) (returns old value or null), remove(k), keys(), values(), size(), isEmpty(). Sorted maps: array + binary search, skip list, BST. Unsorted: hash table.

### Hash tables
- Hash function h maps keys into [0, N − 1], e.g. h(x) = x mod N. Bucket array of size N.
- **Collision:** two keys hash to the same cell.

| Strategy | Probe sequence | Notes |
|---|---|---|
| Separate chaining | linked list per cell | simple, extra memory. **Java HashMap** uses it |
| Linear probing | i, i+1, i+2, … (mod N) | **primary clustering**. Deleted cells get a marker "A" (available) |
| Quadratic probing | i + j² (mod N) | avoids primary clustering, causes **secondary clustering**, **may fail to find an empty cell** |
| Double hashing | i + j·d2(k) (mod N) | d2(k) = q − (k mod q), q < N, **both prime**, d2 never 0, N prime so all cells can be probed. Best when collisions are likely |

- **Load factor α = n/N.** Linear-probing search probes ≈ ½(1 + 1/(1 − α)). Keep α < 0.5 for open addressing → expected O(1) search/insert/remove. As α → 1, probes → ∞.
- **Rehashing:** when the table is too full, build a bigger table (prime size, e.g. 13 → 23) and reinsert everything.
- **Java HashMap:** separate chaining, default capacity **16**, default load factor **0.75**.
- **Advanced hashing:** Cuckoo (two tables, displace occupant to the other table; low load means rarely more than O(log N) displacements, rebuild if too many). Perfect hashing (worst-case O(1) search). Hopscotch (linear-probing idea, item stays within max_dist of home). Universal hashing (hash function picked at random from a family, O(1) operations). Extendible hashing (huge disk-based data, directory of disk blocks, search in at most 2 disk accesses).

### Priority queues
- Entries (key, value). Ops: insert(k, x), removeMin(), min(). Keys compared by a **Comparator**: compare(a, b) < 0, = 0, > 0.
- Implementations: sorted list (min/removeMin O(1), insert O(n)); unsorted list (insert O(1), min O(n)); **heap (insert and removeMin O(log n))**.
- Uses: Huffman coding, search algorithms, OS scheduling, sorting, selection.

### Trees and binary heaps
- Terms: root, internal node (has a child), external node/leaf, depth (number of ancestors), height (max depth), ancestor, descendant, subtree.
- **Heap = heap-order** (key(v) ≥ key(parent(v)), so min at the root) **+ complete binary tree** (levels 0 … h−1 full, last level filled left to right). Last node = rightmost node at depth h.
- Height of a heap with n keys is **O(log n)** (⌊log₂ n⌋).
- **Insert:** put at the new last node, **upheap** (swap with parent while smaller). O(log n).
- **removeMin:** move the last node's key to the root, delete the last node, **downheap** (swap with the smaller child). O(log n).
- **Array form:** index 0 unused, root at 1, children of i at **2i** and **2i + 1**, parent at **⌊i/2⌋**. Insert at n+1, removeMin from rank 1.
- **Bottom-up construction: O(n)** (merge pairs of heaps, downheap the new root, log n phases). Faster than n inserts (O(n log n)).
- **d-heap:** height O(log_d n), still O(log n) ops; a 4-heap may beat a binary heap in practice.
- **Other heaps:** leftist (not necessarily balanced), skew (self-adjusting leftist; O(n) worst, O(log n) amortized), binomial queue (a forest of heaps), Fibonacci heap (forest; removeMin O(log n) amortized, other ops O(1) amortized).
- **Java PriorityQueue** (java.util) is a min-heap: add(e), poll(), optional Comparator.

### Applications in the chapter
- **Selection (k smallest):** naive sort O(n log n); heap-based: build O(n) + k removeMins O(k log n) = **O(n + k log n)**.
- **Word frequencies:** hash table with word as key and count as value.

---

## 3. Search trees (Ch 3)

### Binary trees
- Each internal node has ≤ 2 ordered children (exactly 2 for a **proper** binary tree).
- Proper binary tree with n nodes, e external, i internal, height h:
  **e = i + 1**, n = 2e − 1, h + 1 ≤ e ≤ 2ʰ, h ≤ i ≤ 2ʰ − 1, log(n + 1) − 1 ≤ h ≤ (n − 1)/2.
- Traversals: **preorder** (node, L, R), **inorder** (L, node, R), **postorder** (L, R, node). Euler tour visits internal nodes 3 times. Postorder evaluates an arithmetic expression tree; inorder prints it.
- Uses: arithmetic expression trees, decision trees.

### Binary search trees (BST)
- key(left subtree) ≤ key(v) ≤ key(right subtree). **Inorder = sorted order.**
- Insert: search, then add at the leaf reached.
- Delete: (1) node has a leaf child → splice it out; (2) two internal children → **copy the inorder successor** (leftmost node of the right subtree) into v, then delete the successor.
- Height O(log n) best/average, **O(n) worst** (sorted insertions build a chain). So find/insert/remove are **O(n) worst case**.

### AVL trees
- BST where, for every node, the heights of the two child subtrees differ by **at most 1**. Height O(log n).
- **Insert:** BST insert, walk up, at the first unbalanced node z let y = child, x = grandchild on the path, do **restructure(x)** (trinode). Same direction (LL/RR) → single rotation; zig-zag (LR/RL) → double rotation. **One restructure fixes the tree.**
- **Delete:** BST delete, walk up from the parent w, at unbalanced z take y = taller child, x = taller child of y (ties: same side as y → single rotation), restructure. **May need repeating up to the root.**
- Search, insert, remove: **O(log n) worst case**. A restructure is O(1).

### Multi-way and (2,4) trees
- Multi-way node with d children stores d − 1 keys; inorder visits keys in order.
- **(2,4) tree:** every internal node has ≤ 4 children (2-node, 3-node, 4-node), all external nodes at the same depth. Height O(log n).
- B-trees generalise this idea for disks (databases, file systems).

### Red-black trees
Properties:
1. **Root** is black.
2. **External** nodes (leaves/NIL) are black.
3. **Internal:** a red node's children are black (no red-red).
4. **Depth:** every leaf has the same black depth.

Height ≤ 2 × height of the matching (2,4) tree = O(log n). Search, insert, delete all **O(log n)**. **Java TreeMap and TreeSet are red-black trees.**

**Insertion:** insert as in a BST, colour the new node z **red** (black if it is the root). If parent v is black, done. If v is red (double red), look at the uncle u:
- **Uncle black (or a leaf) → restructure:** trinode on z, v, grandparent. The middle key becomes the subtree root and is black, the other two are red. Done.
- **Uncle red → recolour:** v and u become black, grandparent becomes red (stays black if it is the root). Can push the double red up; repeat.

**Deletion:** BST delete (two children → copy inorder successor). Let v be the removed internal node, r the child that replaces it.
- v or r red → colour r black. Done.
- Both black → r is **double black**. Let y be r's sibling:
  - **Case 1, y black with a red child:** restructure. The new middle node takes the old parent's colour, its two children become black. Done.
  - **Case 2, y black with two black children:** recolour y red. If the parent was red, make it black and stop; if it was black, the parent becomes double black and you repeat upward.
  - **Case 3, y red:** adjustment (rotate y above the parent, swap their colours), then Case 1 or 2 applies.

**Exam example, solved** (tree: 9B; 4R with children 2B, 6B; 6B has right child 7R; 15B with children 12R, 21R).
Insert 5 → goes left of 6, parent is black, so it stays red. Delete 15 → copy successor 21 into that node, remove the red leaf 21, no fix needed.
In-order answer: **2(B) − 4(R) − 5(R) − 6(B) − 7(R) − 9(B) − 12(R) − 21(B)**.

### Splay trees
- BST that stores **no balance info**. After every access the node is **splayed** to the root with rotations:
  - **zig:** x's parent is the root → one rotation.
  - **zig-zig:** x and its parent are both left (or both right) children → rotate the parent first, then x.
  - **zig-zag:** x is a left child of a right child (or the reverse) → rotate x twice.
- When to splay: **search** → the node found (or the last node reached); **insert** → the new node; **delete** → the **parent** of the removed node.
- **O(log n) average (amortized), O(n) worst case.** Frequently used keys stay near the root.

### wavl trees: optional, **not in the exam**.

### Summary table
| Tree | Search / insert / delete (average) | Worst case |
|---|---|---|
| BST | O(log n) | O(n) |
| AVL | O(log n) | O(log n) |
| Red-black | O(log n) | O(log n) |
| Splay | O(log n) | O(n) |

---

## 4. Sorting (Ch 4)

| Algorithm | Best | Average | Worst | In-place? | Stable? | Slide note |
|---|---|---|---|---|---|---|
| Selection | n² | n² | n² | yes | no | small data (< 1K) |
| Insertion | **n** | n² | n² | yes | yes | small data (< 1K), good on nearly sorted |
| Bubble | | n² | n² | yes | yes | simple, slow |
| Shellsort | | depends on gap sequence | Hibbard (1, 3, 7, …, 2ᵏ−1) O(n^1.5), others O(n^4/3) | yes | no | academic interest only |
| Heapsort | n log n | n log n | n log n | **yes** | no | large data (1K–1M) |
| Mergesort | n log n | n log n | n log n | no | **yes** | huge data (> 1M), sequential access |
| Quicksort | n log n | n log n | **n²** | **yes** | no | large data (1K–1M), fastest in practice |
| Bucket sort | | | O(n + N) | no | **yes** | keys in [0, N−1] |
| Radix sort | | | O(d(n + N)) | no | yes | d-tuples / d-digit keys |
| Counting sort | | | O(n + N) | no | | small integer range |

- **Divide and conquer:** divide, recur, conquer. Base case size 0 or 1.
- **Mergesort:** split in half, sort halves, merge in O(n). Tree height log n, O(n) work per level → O(n log n). In-place mergesort is impractical. **Java Collections.sort** uses a (stable) mergesort.
- **Quicksort:** pivot x, partition into L (< x), E (= x), G (> x), recurse on L and G. **Worst case** when the pivot is always the min or max (e.g. sorted input with a last-element pivot) → n(n−1)/2 → O(n²). **Average:** a call is "good" (both sides < 3s/4) with probability ½, expected height O(log n) → O(n log n). Random pivot avoids the bad case. **Java Arrays.sort** uses dual-pivot quicksort (faster than single pivot).
- **In-place quicksort** (slides): pivot = last element; l moves right past elements ≤ pivot, r moves left past elements ≥ pivot, swap S[l] and S[r] while l < r; at the end swap S[l] with the pivot. Recurse on [a, l−1] and [l+1, b].
- **Heapsort:** PQ-sort with a heap. In-place version: phase 1 grows a heap inside the array left to right; phase 2 removes the top and puts it at the end. Increasing order uses a **max-heap** (reverse comparator).
- **Comparison-based lower bound Ω(n log n)** (decision tree of height log n!): optional, **not in the exam**.

### Selection
- **Quickselect** (randomized prune-and-search): partition into L, E, G; if k ≤ |L| recurse on L; if k ≤ |L| + |E| return pivot; else recurse on G with k − |L| − |E|. **O(n) average**; worst case can also be made O(n) (deterministic) but constants are large.
- **Lower bounds (comparisons):** min: **n − 1**; two smallest: **n + ⌈log n⌉ − 2**; median: **3n/2 − O(log n)**; min and max: **3n/2 − 2**.

### Index-based sorts
- **Bucket sort:** put each (k, o) into bucket B[k], then read buckets 0 … N−1 in order. O(n + N), **stable**.
- **Radix sort:** bucket sort on each digit from **least significant to most significant** (needs a stable inner sort). O(d(n + N)). If d is constant and N = O(n) → **O(n)**.
- **Counting sort:** N counters, count occurrences, rewrite the array from the counters. O(n + N), O(n) if N = O(n). Strings must be mapped to integers.

---

## 5. Instructor's own sample questions (from the Ch 4 slides)

1. **Leaderboard, millions of players, list the top ten →** Heap (build O(n), extract 10 in O(k log n)).
2. **Hash table where collisions are likely; reduce clustering so items that collided before are less likely to collide again →** Double hashing.
3. **Real-time stock app, frequent lookups and updates, fast access to frequently queried stocks →** Splay tree (hot keys sit near the root). If the question stresses guaranteed worst-case time for every request, the answer is a red-black tree.

---

## 6. Practical applications (the instructor said to research these)

| Structure / algorithm | Real uses |
|---|---|
| Binary search | dictionary lookup, searching sorted indexes, `Arrays.binarySearch` |
| Prefix averages | moving averages in financial analysis |
| MCSS | best time window for profit (stock gains), signal and DNA segment analysis |
| Hash table | caches, symbol tables in compilers, database indexes, spell checkers, word counting, sets of visited items |
| Priority queue / heap | OS process scheduling, Huffman coding, Dijkstra / A* search, event simulation, top-k queries, median streams |
| BST | in-memory sorted maps, range queries |
| AVL tree | lookup-heavy workloads with few updates (strictest balance → shortest searches) |
| Red-black tree | Java TreeMap/TreeSet, C++ std::map, Linux kernel scheduler; insert/delete-heavy workloads (fewer rotations than AVL) |
| Splay tree | caches and any access pattern where a few keys are hot (recently used items stay at the top) |
| (2,4) / B-trees | databases and file systems (disk blocks) |
| Mergesort | external sorting of data that does not fit in memory, sorting linked lists, stable sorting |
| Quicksort | general-purpose in-memory sorting of large arrays |
| Heapsort | guaranteed O(n log n) with O(1) extra memory (embedded systems), partial sorts / top-k |
| Insertion sort | small or nearly sorted arrays (used inside hybrid sorts) |
| Bucket / counting / radix | integer keys in a small range: grades 0–100, ages, postal codes, IDs, fixed-length strings |
| Quickselect | median or k-th smallest without sorting (statistics, percentiles) |

---

## 7. Two-week plan (today is Fri 9 Oct)

| Days | Focus |
|---|---|
| Oct 9–11 | Ch 1: definitions, finding c and n0, loop complexities, MCSS |
| Oct 12–14 | Ch 2: hashing by hand (linear, quadratic, double), heap insert/removeMin in array form |
| Oct 15–18 | Ch 3: BST delete, AVL insert/delete rotations, red-black insert/delete cases, splaying. Do every tree problem in the practice set twice |
| Oct 19–20 | Ch 4: complexity table from memory, trace in-place quicksort, merge, radix and counting sort |
| Oct 21 | Full practice set under time (2 h), mark with the answer key |
| Oct 22 | Re-do only what you got wrong; review sections 5 and 6 |

**Exam tips.** Level II short answers are the trickiest marks: write the tree after every step on the draft paper, and double-check colours with the four red-black properties before writing the final traversal. For Big-O proofs, always state c and n0 explicitly.
