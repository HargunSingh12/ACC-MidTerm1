# Mid-Term 2: complete notes (Ch 5–8)

COMP 8547 · Exam Fri 20 Nov 2026 · Assumed format: 10 MCQ L-I, 10 MCQ L-II, 10 short answer L-I, 5 hands-on L-II (final answer only)

Everything here is taken from the slides. ⭐ marks things that are very likely to be asked.

---

# Chapter 5: Advanced Design and Analysis

## 5.1 Recursion
- **Definition:** a method that calls itself.
- **Parts:**
  - **Base case:** no recursion happens here.
  - **Recur:** calls itself, and every call must eventually reach a base case.
- **Pros:** easy to design for problems that are defined recursively.
- **Cons:** often **very inefficient**. You analyse the cost with **recurrence equations**.
- Factorial: `if n = 0 return 1 else return n · factorial(n−1)`
- **Recursive Fibonacci:** `if k = 0 or 1 return k, else rF(k−1) + rF(k−2)` runs in **exponential time** ⭐
  - Number of calls for rF(n) = **2·F(n+1) − 1**. So rF(6) makes 25 calls and rF(10) makes **177**.
  - F: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89

## 5.2 Divide and conquer ⭐
1. **Divide:** split the input S into two or more **disjoint** subproblems S₁, S₂, …
2. **Recur:** solve each subproblem recursively.
3. **Conquer:** combine the sub-solutions into a solution for S.
- The base case is a subproblem of constant size. You analyse it with recurrence equations.
- **Merge sort:** T(n) = 2T(n/2) + cn, which gives **Θ(n log n)**.
  - With a recursion tree: depth i has 2ⁱ nodes, each of size n/2ⁱ, so the cost per level is cn. There are log n levels, so the total is **cn + cn log n**.

## 5.3 Master theorem, basic form ⭐⭐⭐
For **T(n) = a·T(n/b) + O(nᵈ)**, where a > 0, b > 1 and d ≥ 0:

| Compare | Result |
|---|---|
| d > log_b a | **O(nᵈ)** |
| d = log_b a | **O(nᵈ log n)** |
| d < log_b a | **O(n^(log_b a))** |

- **a** = the number of subproblems, **n/b** = the size of each one, **nᵈ** = the work done outside the recursion.
- log_b a means "b to what power gives a?" (log₄2 = ½ because √4 = 2). **Don't flip it.**

## 5.4 Master theorem, advanced form ⭐⭐
For **T(n) = a·T(n/b) + Θ(nᵏ logᵖ n)**, where a ≥ 1, b > 1, k ≥ 0 and p is a real number:

1. **a > bᵏ:** Θ(n^(log_b a))
2. **a = bᵏ:**
   - (a) p > −1: Θ(n^(log_b a) · log^(p+1) n)
   - (b) p = −1: Θ(n^(log_b a) · log log n)
   - (c) p < −1: Θ(n^(log_b a))
3. **a < bᵏ:**
   - (a) p ≥ 0: Θ(nᵏ logᵖ n)
   - (b) p < 0: Θ(nᵏ)

**Worked examples from the slides and exercises:**

| Recurrence | a, b, k, p | Case | Answer |
|---|---|---|---|
| T(n/2) + 1 (binary search) | 1, 2, 0, 0 | 2a | **log n** |
| 2T(n/2) + n (merge sort) | 2, 2, 1, 0 | 2a | **n log n** |
| 3T(n/2) + n² | 3, 2, 2, 0 | 3a | **n²** |
| 3T(n/2) + log² n | 3, 2, 0, 2 | 1 | **n^(log₂3)** |
| 2T(n/2) + n log² n | 2, 2, 1, 2 | 2a | **n log³ n** |
| 8T(n/2) + n² | | d < log₂8 = 3 | **n³** |
| 3T(n/4) + n² | | d = 2 > log₄3 | **n²** |
| T(n/4) + log n | 1, 4, 0, 1 | 2a | **log² n** |
| 4T(2n/3) + log² n | b = 3/2 | 1 | **n^(log_{1.5}4) ≈ n^3.42** |
| 9T(n/3) + n² | | d = log₃9 = 2 | **n² log n** |
| 2T(n/4) + √n | | d = ½ = log₄2 | **√n log n** |

- **The theorem can't be used** when a isn't a constant (e.g. 2ⁿ·T(n/2)), or when f(n) isn't of the form nᵏ logᵖ n (e.g. nⁿ). ⭐ This is the slides' Example 6.
- **h(n)/u(n) method** (the one you use): T(n) = n^(log_b a) · u(n), where **h(n) = f(n) / n^(log_b a)**. If h(n) = (log n)ⁱ, then u(n) = (log n)^(i+1) / (i+1).

## 5.5 Dynamic programming ⭐⭐⭐
**The 4 properties needed:**
1. **Simple subproblems:** each one is defined by a few variables (j, k, l, m…).
2. **Subproblem optimality:** the global optimum is built from optimal subproblems.
3. **Subproblem overlap:** subproblems aren't independent, they overlap.
4. **Bottom-up construction:** small subproblems are solved first and stored in a table.

**DP Fibonacci:** A[0] = 0, A[1] = 1, then for i = 2..k, A[i] = A[i−1] + A[i−2]. That's **O(k)**, linear.

**DP vs recursion** ⭐

| Dynamic programming | Recursion |
|---|---|
| **Bottom-up**: small subproblems first | **Top-down**: tries the whole problem and calls smaller ones |
| Each subproblem solved **once** | Subproblems may be solved **many times** |
| The solution is **difficult** to formulate | The solution is **easy and natural** |
| **Polynomial** time | May be **exponential** |

**Problems solved with DP:** LCS, edit distance, bio-sequence alignment (global or local, pairwise or multiple), all-pairs shortest path, travelling salesman, matrix chain multiplication, optimal BSTs, 0-1 knapsack, assembly-line scheduling, multi-level thresholding, HMM parameters, speech recognition.

## 5.6 Longest common subsequence (LCS) ⭐⭐⭐
- A **subsequence** is a set of characters that are **not necessarily contiguous** but keep their order.
- **L[i,j]** = the LCS length of X[0..i] and Y[0..j]. L[−1,k] = L[k,−1] = 0.
- **If xᵢ = yⱼ:** L[i,j] = L[i−1,j−1] + 1 (take the diagonal and add 1).
- **If xᵢ ≠ yⱼ:** L[i,j] = max(L[i−1,j], L[i,j−1]) (the larger of up and left).
- **Time O(nm)**, or **O(n²)** if both strings have the same length. Recursive LCS is **exponential**.
- Trace back from the bottom-right corner to get the actual subsequence. **There can be more than one LCS.**
- Applications: index terms in web pages, DNA and protein alignment.
- Examples:
  - AGCCTAGT vs GACTCAT: **5** (ACTAT, GCTAT)
  - transposition vs transponder: **8**
  - ABCBDAB vs BDCABA: **4**
- Self-check: the numbers never decrease going right or going down.

## 5.7 Edit distance ⭐⭐⭐
- The **minimum number of operations** needed to turn X into Y. It's a generalisation of LCS.
- **3 operations, each costing 1:** **substitution, insertion, deletion**.
- C[i,0] = i, C[0,j] = j.
- C[i,j] = min( C[i−1,j] + 1, C[i,j−1] + 1, C[i−1,j−1] + (0 if the letters are equal, else 1) )
  - The slides write the last term as +1 − δ, where δ = 1 if the letters are equal.
- **Time O(nm)**. You can generalise it to other costs, e.g. different costs per symbol.
- Examples:
  - excused → exhausted = **3** (substitute c with h, insert a, insert t)
  - kitten → sitting = 3
  - sunday → saturday = 3
  - transposition → transponder = 6
  - "" → word of length k = **k**
- **Applications:** DNA and protein alignment, **spellchecking**, document comparison (plagiarism, similar programs, similar web pages).
- **Spellchecker:** if w is in dictionary D, it's spelled correctly. Otherwise compute the edit distance from w to every word in D, **rank** by distance and suggest the **top k**. Example: hoyse → house, horse, hose (each distance 1).

---

# Chapter 6: Graph Algorithms

## 6.1 Definitions ⭐
- **Graph G = (V, E):** V is a set of vertices, and E ⊆ V × V.
- **Directed:** ordered pairs, so (u,v) ≠ (v,u). **Undirected:** unordered pairs {u,v}.
- **Path:** a sequence of vertices. **Simple path:** all vertices are different. **Cycle:** the first vertex equals the last.
- **Acyclic graph:** has no cycles. **DAG:** directed acyclic graph.
- **Adjacent:** w is adjacent to v if (v,w) ∈ E. Written Adj[v].
- **Tree:** an undirected acyclic graph. **Forest:** a disjoint set of trees.
- **Reachable / connected:** u is reachable from v if there's a path from v to u. A graph is **connected** if there's a path between every pair of vertices.
- **Spanning tree:** a subgraph that is a tree and contains **all vertices**. **Spanning forest:** spanning trees of an unconnected graph.
- **Sparse:** |E| ≪ |V|² (e.g. a co-authorship network). **Dense:** |E| ≈ |V|² (e.g. a protein interaction network).
- **Weighted graph:** each edge has a weight w(u,v). It can be an object, like flight information.

## 6.2 Representations ⭐⭐

| | Adjacency list | Adjacency matrix |
|---|---|---|
| Structure | an array of \|V\| linked lists, Adj[u] | a \|V\| × \|V\| matrix, aᵢⱼ = 1 if there's an edge |
| **Space** | **O(V + E)** | **O(V²)** |
| Best for | **sparse** graphs | **dense** graphs |
| Note | an undirected graph has **2E** list nodes | a V = 8 graph has 64 entries |

## 6.3 Spanning trees ⭐⭐⭐
- A spanning tree G'(V', E') has **V' = V** and **E' = |V| − 1**, has **no cycles**, and **can't be disconnected**.
- A connected graph can have **more than one** spanning tree.
- **Cycle graph** (V = E, one closed cycle): **n(ST) = V**.
- **Complete graph: n(ST) = V^(V−2)** (Cayley's formula). K₄ = 16, K₅ = 125, K₆ = 1296.
- If several edges have the **same weight**, there can be **more than one MST**.
- Application: removing network loops (Paul's LAN scenario).

## 6.4 MST: Prim vs Kruskal ⭐⭐⭐
- **MST:** for a connected, undirected, weighted G, it's a spanning tree with the **minimum total weight**. **Both algorithms are greedy.**

| | **Prim** | **Kruskal** |
|---|---|---|
| Idea | grow **one tree** from any vertex, adding the lightest edge that leaves the tree | **sort all edges**, then add the lightest one that **doesn't form a cycle** |
| Order | edges in **contiguous** order | edges **not** in contiguous order |
| Intermediate result | **always a tree** | a **forest** (not necessarily a tree) |
| Disconnected graphs | **doesn't work** | **works** (gives a spanning forest) |
| Data structure | priority queue (key[], π[]) | Make-Set, Find-Set, Union (disjoint sets) |
| **Time** | **O(E log V)** with a binary heap, **O(E + V²)** with an array | **O(E log E)**, sorting dominates |
| Stop when | all vertices are in the tree | **V − 1 edges** have been added |

- Prim pseudocode: key[u] = ∞, key[r] = 0, Q = V (a heap). Repeat: u = Extract-Min(Q). For each v ∈ Adj[u], if v ∈ Q and w(u,v) < key[v], set π[v] = u and key[v] = w(u,v).
- Kruskal: a **safe edge** is the lightest edge that connects two different trees in the forest. `if Find-Set(u) ≠ Find-Set(v): A = A ∪ {(u,v)}, Union(u,v)`

## 6.5 BFS ⭐⭐⭐
- Uses a **queue**. Colours: white (unvisited), gray (discovered), blue/black (done).
- Computes **d[v], the shortest number of edges** from s, and builds a **breadth-first tree**.
- Works on directed and undirected graphs, but only finds shortest paths in **unweighted** graphs.
- **Time O(V + E).**
- Applications: **exploring a maze** (passages are edges, intersections are vertices) and finding a goal. BFS never visits a passage twice.

## 6.6 DFS ⭐⭐⭐
- Goes **deep first**. Uses **recursion**, or a **stack** in the non-recursive version.
- Records d[u] (discovery time) and f[u] (finish time). Colours: white, gray, black.
- Gives both **preorder and postorder** traversals.
- **Time O(V + E).** Works on directed and undirected graphs.
- Trace tip: always go to the **first unvisited neighbour** in the given order, and backtrack only when there are none left.

## 6.7 Shortest paths: Dijkstra ⭐⭐⭐
- **Single-source**, on a weighted directed graph with **non-negative weights**. It's **greedy**.
- Initialise: d[v] = ∞, π[v] = nil, d[s] = 0. Repeat: u = Extract-Min(Q), S = S ∪ {u}, and relax each neighbour.
- **Relax(u,v,w):** if d[v] > d[u] + w(u,v), then d[v] = d[u] + w(u,v) and π[v] = u.
- **Time O(E + V log V)** with a **Fibonacci heap**.
- Fails with **negative** weights.
- **Variants:** single-destination, single-pair, all-pairs.
- Trap to watch for: the direct edge isn't always the shortest. A→C→B (1 + 2) beats A→B (4).

## 6.8 Connected components ⭐
- Run DFS. If it doesn't reach every vertex, **restart DFS** on an unvisited one. The result is a **spanning forest**.
- **Time O(V + E).**
- A spanning forest with V vertices and k components has **V − k edges**.

## 6.9 Applications
- **Protein interaction networks** (the interactome): connected components give sub-networks with related functions. **Hubs** are vertices with many connections. Also clusters, visualisation and graph alignment. Haemoglobin is made of 4 interacting proteins.
- **IMDB graph:** vertices are movies and performers, and edges connect each movie to its performers (movies.txt).
- **Java library:** algs4 (Princeton), with DFS, BFS, shortest paths, MST and connected components.

---

# Chapter 7: Text Processing

## 7.1 String terms ⭐⭐
- **String:** a finite sequence of n characters from an alphabet Σ, e.g. {A,C,G,T} or {a–z, A–Z}.
- **Null string:** length 0, written ε.
- **Substring:** **consecutive** characters sᵢ…sⱼ.
- **Prefix:** a substring that **starts at index 0**. **Suffix:** a substring that **ends at n−1**.
- **Subsequence:** characters that are **not necessarily consecutive**, i₁ < i₂ < … < iₖ.
- Usually stored as an **array of characters**.
- Applications: the Internet and search, computational biology (DNA, RNA with U instead of T, proteins with 20 amino acids), email, compression and encryption, compilers, word processing.

## 7.2 Pattern matching
- Given text **T of length n** and pattern **P of length m**, find substrings of T that match P.
- Algorithms: brute force, **Boyer-Moore**, **KMP**, Rabin-Karp.

## 7.3 Brute force ⭐⭐
- Try every shift i = 0 … n − m, comparing **left to right**, until there's a match or every shift has been tried.
- **Worst case O(nm)**, e.g. T = aaa…ah and P = aaah. This happens in images and DNA, but is unlikely in English.
- Exact counting:
  - **n − m + 1** shifts.
  - If every shift matches m − 1 characters then fails, the count is **m(n − m + 1)**.
  - If every shift fails on the first character, the count is **n − m + 1**, which is O(n).

## 7.4 Boyer-Moore ⭐⭐⭐
- **Looking-glass heuristic:** compare P with T **moving backwards**, from right to left.
- **Character-jump heuristic:** on a mismatch at T[i] = c:
  - If P contains c, shift P to align the **last occurrence** of c in P with T[i].
  - Otherwise, shift P so that P[0] lines up with T[i+1].
- **Last-occurrence function L(c):** the largest index of c in P, or **−1** if c isn't in P.
  - P = rithm gives L(r) = 0, L(i) = 1, L(t) = 2, L(h) = 3, L(m) = 4.
  - P = abacab gives L(a) = 4, L(b) = 5, L(c) = 3.
- **Shift rule:** l = L[T[i]], then **i = i + m − min(j, 1 + l)** and j = m − 1.
  - Case 1, j ≤ 1 + l: i increases by m − j.
  - Case 2, 1 + l ≤ j: i increases by m − (1 + l).
- **Worst case O(nm + |Σ|)**, e.g. T = aaa…a and P = baaa. It happens in images and low-complexity DNA.
- **Much faster than brute force on English text.**
- Best case: if the text character isn't in P at all, P jumps by m, so there are about **n/m comparisons**.

## 7.5 KMP (Knuth-Morris-Pratt) ⭐⭐⭐
- Compares **left to right** like brute force, but **shifts more intelligently**.
- **Failure function F(j):** the length of the **largest prefix of P[0..j] that is also a suffix of P[1..j]**, i.e. the longest proper prefix that is also a suffix.
  - P = abacab gives F = [0, 0, 1, 0, 1, 2].
  - P = ababac gives F = [0, 0, 1, 2, 3, 0].
  - P = aabaa gives F = [0, 1, 0, 1, 2].
  - P = AAAB gives F = [0, 1, 2, 0].
- **Algorithm:**
  - **Match:** if j = m−1, return i − j. Otherwise i++ and j++.
  - **Mismatch and j > 0:** **j = F[j−1]**, and i stays the same.
  - **Mismatch and j = 0:** i++.
- **The text index i never moves backwards.**
- The failure function takes **O(m)**. The search takes **O(n)**, with at most **2n** loop iterations. Total **O(m + n)**, which is **optimal**.
- **Main difference from Boyer-Moore:** KMP compares left to right and preprocesses with the failure function, so its worst case is O(n+m). BM compares right to left and preprocesses with the last-occurrence function, so its worst case is O(nm + |Σ|) but it's usually faster on English.

## 7.6 Tries ⭐⭐⭐
- KMP and BM **preprocess the pattern**. A trie **preprocesses the text**, which helps when the text is large or searched often (books, web pages). Queries take time proportional to the **pattern size**.
- **Standard trie** for a set of strings S:
  - Every node except the root is labelled with one character.
  - Children are in **alphabetical order**.
  - Each path from the root to an external node spells a string in S.
- **Space O(n)**, where n is the total length of the strings.
- **Search, insert and delete each take O(dm)**, where d is the alphabet size and m is the length of the string. With a direct child array the per-character cost is O(1), so it's O(m).
- **Counting nodes:** the number of distinct prefixes, not counting the root.
  - {bear, bell, bid, bull, buy, sell, stock, stop} has 21 nodes.
  - Inserting a word adds one node for each character after the longest prefix that's already in the trie.
- **Word matching:** insert the words of the text, and store at each leaf the indices where that word starts.

## 7.7 Compressed tries ⭐⭐
- **Every internal node has at least 2 children.** Chains of single-child nodes are merged into one node, e.g. b → e → (ar, ll), id, u → (ll, y).
- **Inserting:** split an edge at the **first differing character**. For example, STONE + STOVE gives a shared **STO** with branches **NE** and **VE**.
- **Compact representation:** each node stores **(i, j, k)**, meaning label = **S[i][j..k]**. It uses **O(s)** space, where s is the number of strings. It's an auxiliary index structure.
  - S[1] = bear gives the "ar" node (1,2,3).
  - S[2] = sell gives the "ell" node (2,1,3).
- Search in a compressed trie is **not necessarily faster** than in a standard trie.

## 7.8 Ternary search trie (TST) ⭐
- A compact version of a **d-way trie**. Each node has a character c and **3 links**: keys < c, keys starting with c (the middle link), and keys > c.
- On a match you follow the **middle** link. A miss ends quickly at a null link.
- Searches are more efficient than in a d-way trie.

## 7.9 Other topics
- **Suffix trie:** the **compressed trie of all suffixes** of T.
- **Text compression:** tries are used for **Huffman coding**. Advanced methods include PPM, LZ/LZW, block sorting and grammar-based compression.
- **Prefix code:** no codeword is a prefix of another. Huffman codes are prefix codes.
- **Inverted index (inverted file)** ⭐:
  - A map of entries (w, L), where w is a word (index term) and L is the list of its occurrences in web pages.
  - It's implemented as a **trie**, where each leaf points to an occurrence list stored **outside** the trie.
  - A simple search engine looks up the keyword, gets L, and shows the top k pages by number of occurrences.
- **Java classes:** BruteForceMatch, BoyerMoore, KMP, TrieST (put and get), TST.

---

# Chapter 8: Languages

## 8.1 Basics ⭐⭐
- **Language:** a systematic way to communicate, made of symbols, words and rules. Examples are natural languages (English, French…) and programming languages (C, Java, HTML, XML, Python…).
- **Formal language over an alphabet:** a subset of all the strings that can be made from that alphabet.
- **Alphabet Σ:** a finite, **non-empty** set of symbols, e.g. {0,1}, {0..9}, {a..z}, or the 256 ASCII characters.
- **String (word):** a finite sequence of symbols from Σ.
- **Language L ⊆ Σ\***, where Σ\* is the set of **all** strings including ε.
  - Examples: binary representations of primes {10, 11, 101, …}, binary strings ending in 11, strings with equal numbers of 0s and 1s, and multiples of 4 in binary {100, 1000, 1100, …}.
- English as a language: L = {w | w is grammatically correct English text}. C as a language: L = {w | w is a syntactically correct C program}.
- **Hierarchy of programming languages,** from high to low: natural language, problem-oriented language, high-level (Java, C++, Python), **assembly**, **machine**.

## 8.2 Chomsky hierarchy ⭐⭐⭐
**Regular ⊂ Context-free ⊂ Context-sensitive ⊂ Unrestricted**

| Level | Language | Grammar rule α → β | Example | Recognised by |
|---|---|---|---|---|
| **3** | **Regular** | \|α\| = 1, \|β\| ≥ 1 | A → 0A \| ε | **Finite automata**, regular expressions |
| **2** | **Context-free (CFL)** | \|α\| = 1, \|β\| ≥ 1 | A → 0A1 \| ε | **Pushdown automata (PDA)** |
| **1** | **Context-sensitive (CSL)** | \|α\| ≤ \|β\| | S → AC0, C0 → 00C, A → 00 | **Linear bounded automata (LBA)** |
| **0** | **Unrestricted** | n, m ≥ 1 (any) | {0ⁱ \| i is a power of 2} | **Turing machines** |

- **Most programming languages are context-free**, with some patches such as reserved keywords. ⭐
- CSLs have **not much practical use**.
- {0ⁿ1ⁿ} is **context-free but not regular**.

## 8.3 Regular expressions ⭐⭐⭐
- A **declarative** way to describe a **regular language**.
- Built from letters of the alphabet, ε and operands.
- **Operations:** **union r|s**, **concatenation rs**, **closure r\***, and **parentheses (r)**.

| RE over {0,1} | Language |
|---|---|
| (0\|1)\* | all binary strings, including ε |
| 0\*1 | zero or more 0s followed by a 1: 1, 01, 001, … |
| 0(0\|1)\*1 | starts with 0 and ends with 1 |
| (0\|1)\*1(0\|1)\* | contains at least one 1 |

- **Keyword example:** `(micro)?( |-)?(array|chip)(s)?` matches microarray, micro-array, micro arrays, chips, … but not microkarray or bigarray.

## 8.4 Tools and applications ⭐
- **Applications:** compilers (finding tokens before syntax analysis), pattern scanning (`ls data*.txt`, grep), **validation** (phone numbers, addresses, emails, URLs), pattern recognition (DNA and proteins), speech and text processing.
- **Tools:** command lines (DOS, Windows, Unix: dir, ls, rm, mv…), **grep**, **Java Regex**, XML for modelling data, and **Lex** (Unix) and **JFlex** (Java), which pass **lexemes/tokens to the syntax analyser (parser)**.
- **Compilers and text processing share:** lexical analysis (tokens), syntax analysis (parsing) and translation.

## 8.5 Java Regex ⭐⭐⭐
- The package is **java.util.regex**, and its syntax is **similar to Perl**.
- **3 classes:**
  - **Pattern:** a compiled RE. It has **no public constructors**, so you create one with **Pattern.compile()**.
  - **Matcher:** the engine that matches against an input. It also has **no public constructors**. You get one with **pattern.matcher(input)**.
  - **PatternSyntaxException:** an **unchecked** exception for a bad pattern.
- **Pattern methods:**
  - compile(regex)
  - **matches(regex, input):** true only if the **whole** input matches
  - **split(input):** `Pattern.compile(":").split("one:two:three:four")` gives 4 items
- **Matcher methods:**
  - **find():** finds the next match
  - **start():** the index where the last match starts
  - **end():** the offset **after** the last matched character
  - **group():** the matched text
- **Metacharacters:** `( [ { \ ^ - $ | ] } ) ? * + .` To match one literally, put **\\** before it (in a Java string, write `"\\d"`).

**Character classes**

| Syntax | Meaning |
|---|---|
| [abc] | a, b or c |
| [^abc] | anything **except** a, b or c (negation) |
| [a-zA-Z] | a range |
| [a-d[m-p]] | **union**, the same as [a-dm-p] (8 characters) |
| [a-z&&[def]] | **intersection**: d, e, f |
| [a-z&&[^bc]] | **subtraction**: a–z except b and c (24 characters) |
| [a-z&&[^m-p]] | a–l and q–z |

**Predefined classes**

| | |
|---|---|
| . | any character |
| \d | a digit, [0-9] |
| \D | a non-digit |
| \s | whitespace, [ \t\n\x0B\f\r] |
| \S | non-whitespace |
| \w | a word character, **[a-zA-Z_0-9]** (the underscore is included) |
| \W | a non-word character |

**Quantifiers**

| Greedy | Reluctant | Possessive | Meaning |
|---|---|---|---|
| X? | X?? | X?+ | 0 or 1 times |
| X* | X*? | X*+ | 0 or more |
| X+ | X+? | X++ | 1 or more |
| X{n} | X{n}? | X{n}+ | exactly n |
| X{n,} | X{n,}? | X{n,}+ | at least n |
| X{n,m} | X{n,m}? | X{n,m}+ | between n and m |

- **Greedy** takes as much as it can, **reluctant** takes as little as it can, and **possessive** takes as much as it can **and never backtracks**.
- Example: find() on "aaaaaaa" (7 a's) gives **2** matches with a{2,3} (aaa, aaa) and **3** with a{2,3}? (aa, aa, aa).

**Boundary matchers**

| | |
|---|---|
| ^ | the beginning of a line |
| $ | the end of a line |
| \b | a word boundary |
| \B | a non-word boundary |
| \A | the beginning of the input |
| \G | the end of the previous match |
| \Z | the end of the input, ignoring a final terminator |
| \z | the end of the input |

**Slide examples** ⭐
- **Canadian postal code:** `[A-Za-z][0-9][A-Za-z]\s?[0-9][A-Za-z][0-9]` matches N9B 3P4, N9B3P4 and n9b3p4.
- **Phone:** `(\d){3}-(\d){3}-(\d){4}` matches 519-253-3000, but **not** 519 253-3000 or (519) 253-3000.
- **Regular languages listed on the slides:** postal codes, phone numbers, emails, URLs, program identifiers, simple arithmetic expressions without parentheses, floating-point numbers, postal addresses, page numbers, HTML tags, keywords.

## 8.6 Grammars ⭐⭐
- **A grammar has 4 parts:** Σ (terminals), N (non-terminals), S (the start symbol) and P (productions).
- **Arithmetic expression grammar:**
  - Σ = {+, *, (, ), a, b, 0, 1}, N = {E, I}, S = E
  - E → I | E+E | E*E | (E)
  - I → a | b | Ia | Ib | I0 | I1
  - **Identifiers must start with a or b.** Valid examples: ab1a * b01 + bab, (a1 + b0) * a.
- **Simplified HTML grammar:** html_document → html_tag → `<HTML> html_content </HTML>`, html_content → head_tag body_tag, plus title, list (`<OL>` and `<LI>`), paragraph (`<P>`), bold `<B>`, italics `<EM>`, and link `<A HREF="url">`.

## 8.7 HTML tools ⭐
- **jsoup:** a free, open-source Java HTML parser. It implements **HTML5** and parses HTML into a **DOM**. It can scrape and parse from a URL, file or string, extract data with DOM traversal or **CSS selectors**, change elements, **clean user input against a whitelist to prevent XSS**, and output tidy HTML.
  - `Jsoup.connect(url).get().text()`
- **Web crawler (robot):** browses the web systematically **without user intervention**.
  1. Start from a reference page.
  2. **Extract all URLs with a regex.**
  3. For each URL, download the page and repeat step 2. Stop once you have the number of pages you want.

---

# Formula sheet (memorise this)

| Thing | Value |
|---|---|
| Recursive Fibonacci | exponential, 2F(n+1) − 1 calls |
| DP Fibonacci | O(k) |
| Merge sort | Θ(n log n) |
| LCS, edit distance | O(nm) |
| Adjacency list / matrix space | O(V+E) / O(V²) |
| BFS, DFS, connected components | O(V+E) |
| Prim (heap / array) | O(E log V) / O(E + V²) |
| Kruskal | O(E log E) |
| Dijkstra (Fibonacci heap) | O(E + V log V) |
| Spanning tree edges | V − 1 |
| Spanning trees of K_V / cycle | V^(V−2) / V |
| Brute force | O(nm) |
| Boyer-Moore | O(nm + \|Σ\|) |
| KMP / failure function | O(n + m) / O(m) |
| Trie space / operations | O(n) / O(dm) |
| Compact compressed trie | O(s) |
