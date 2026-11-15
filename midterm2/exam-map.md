# Mid-Term 2 exam map (Ch 5–8)

Exam: Fri 20 Nov 2026 (to confirm). Assumed format, same as Mid-Term 1: 100 pts / 2 h. 10 MCQ L-I, 10 MCQ L-II, 10 short answer L-I (one word or formula), 5 hands-on L-II (final answer only).

Stars show how likely a topic is to be asked: ★★★ = almost certain, ★ = possible.

---

## Ch 5: Advanced Design and Analysis

| Topic | What to know | Likely |
|---|---|---|
| Master theorem, basic form | T(n) = aT(n/b) + O(n^d). Compare d with log_b a: **d > log_b a gives n^d**, **d = log_b a gives n^d log n**, **d < log_b a gives n^(log_b a)** | ★★★ hands-on |
| Master theorem, advanced form | T(n) = aT(n/b) + Θ(n^k log^p n). Case 1: a > b^k gives n^(log_b a). Case 2 (a = b^k): p > −1 gives n^(log_b a)·log^(p+1) n, p = −1 gives n^(log_b a)·log log n, p < −1 gives n^(log_b a). Case 3 (a < b^k): p ≥ 0 gives n^k log^p n, p < 0 gives n^k | ★★★ |
| When Master does NOT apply | a not constant (e.g. 2^n·T(n/2)), or f(n) not of form n^k log^p n (e.g. n^n) | ★★ MCQ |
| Recursion | base case + recur step; recursive Fibonacci is **exponential**; rF(10) makes **177** calls (formula 2F(n+1) − 1) | ★★ |
| Divide and conquer | divide, recur, conquer; merge sort T(n) = 2T(n/2) + cn = Θ(n log n) | ★★ |
| DP, 4 properties | simple subproblems, subproblem optimality, subproblem overlap, bottom-up construction | ★★★ MCQ |
| DP vs recursion | DP is bottom-up, each subproblem solved once, polynomial. Recursion is top-down, subproblems repeated, may be exponential | ★★★ |
| DP Fibonacci | O(k) time | ★ |
| LCS | if x_i = y_j, L[i,j] = L[i−1,j−1] + 1, else max(L[i−1,j], L[i,j−1]). **O(nm)**. Subsequence need not be contiguous | ★★★ hands-on |
| Edit distance | ops: substitution, insertion, deletion (cost 1 each). C[i,j] = min(up+1, left+1, diag + (0 if equal else 1)). **O(nm)**. First row and column are 0,1,2,… | ★★★ hands-on |
| Applications | spellchecking (rank dictionary words by edit distance, top k), document comparison, DNA alignment | ★★ |

Slide answers worth memorising:
- AGCCTAGT vs GACTCAT: LCS = **5** (ACTAT, GCTAT), edit distance 4
- excused → exhausted: edit distance **3**
- transposition vs transponder: LCS = **8**, edit distance **6**
- 8T(n/2) + n² gives n³. 3T(n/4) + n² gives n². T(n/4) + log n gives log² n. 3T(n/2) + n² gives n². 2T(n/2) + n log² n gives n log³ n

## Ch 6: Graph Algorithms

| Topic | What to know | Likely |
|---|---|---|
| Definitions | path, simple path, cycle, DAG, tree (undirected acyclic), forest, connected, reachable, spanning tree / forest | ★★ MCQ |
| Sparse vs dense | sparse: E ≪ V²; dense: E ≈ V² | ★★ |
| Representations | adjacency list **O(V+E)** space (good for sparse); adjacency matrix **O(V²)** (good for dense) | ★★★ |
| Spanning tree | V' = V, **E' = V − 1**, no cycles, connected | ★★★ |
| Count of spanning trees | cycle graph (V = E): **n(ST) = V**. Complete graph: **V^(V−2)** (Cayley), e.g. K4 = 16 | ★★★ |
| MST uniqueness | equal edge weights can give more than one MST | ★★ |
| Prim | greedy, grow one tree from any vertex, needs connected graph, intermediate result is a tree. **O(E log V)** with binary heap, **O(E + V²)** with array | ★★★ hands-on |
| Kruskal | greedy, sort edges, add if no cycle (Find-Set / Union), works on disconnected graphs (gives a forest), intermediate result is a forest. **O(E log E)**, sorting dominates. Stop at V − 1 edges | ★★★ hands-on |
| BFS | queue, shortest path in **unweighted** graph, **O(V+E)**, colours white/gray/blue (black) | ★★★ |
| DFS | recursion or stack, goes deep, discovery/finish times d[u]/f[u], **O(V+E)** | ★★★ |
| Dijkstra | single-source, **non-negative weights**, greedy, relax: if d[v] > d[u] + w then update. **O(E + V log V)** Fibonacci heap | ★★★ hands-on |
| Shortest path variants | single-source, single-destination, single-pair, all-pairs | ★ |
| Connected components | run DFS, restart on unvisited vertices, gives spanning forest, **O(V+E)** | ★★ |
| Applications | network loops (spanning tree), protein interaction networks (hubs, clusters), IMDB graph, maze with BFS | ★ |

## Ch 7: Text Processing

| Topic | What to know | Likely |
|---|---|---|
| String terms | prefix (starts at 0), suffix (ends at n−1), substring (contiguous), subsequence (not contiguous), null string ε | ★★★ |
| Brute force | try every shift, **O(nm)**, worst case T = aaa…ah, P = aaah | ★★ |
| Boyer-Moore | looking-glass (compare right to left) + character-jump (align last occurrence). Last-occurrence function L(c), −1 if absent. Shift i += m − min(j, 1 + L). **O(nm + \|Σ\|)** worst, fast on English | ★★★ hands-on |
| KMP | left to right, failure function F(j) = longest prefix of P[0..j] that is a suffix of P[1..j]. On mismatch j = F[j−1]. Failure fn **O(m)**, total **O(n + m)**, at most 2n iterations | ★★★ hands-on |
| Standard trie | root empty, children alphabetical, **O(n)** space, search/insert/delete **O(dm)** | ★★★ |
| Compressed trie | every internal node has ≥ 2 children; compact rep uses triples (i, j, k) = S[i][j..k], **O(s)** space; not necessarily faster search | ★★ |
| TST | 3 links: less, equal, greater; follow middle link on match | ★★ |
| Suffix trie | compressed trie of all suffixes of T | ★★ |
| Huffman / encoding trie | tries for compression; prefix code | ★ |
| Inverted index | map (word, list of occurrences), implemented as trie, leaves point to occurrence lists | ★★ |

Slide answers: P = abacab gives F = [0,0,1,0,1,2] and L(a)=4, L(b)=5, L(c)=3. The slide traces use 13 comparisons (BM) and 19 (KMP), on slightly different texts.

## Ch 8: Languages

| Topic | What to know | Likely |
|---|---|---|
| Building blocks | alphabet Σ (finite, non-empty), string/word, language L ⊆ Σ* | ★★★ |
| Language hierarchy | natural > problem-oriented > high-level > assembly > machine | ★ |
| Chomsky hierarchy | **Level 3 Regular** (FA, regex, A → 0A \| ε) ⊂ **Level 2 Context-free** (PDA, A → 0A1 \| ε, most programming languages) ⊂ **Level 1 Context-sensitive** (LBA, α → β with \|α\| ≤ \|β\|) ⊂ **Level 0 Unrestricted** (Turing machine) | ★★★ |
| Regex operators | union r\|s, concatenation rs, closure r*, parentheses | ★★★ |
| Classic regexes | (0\|1)*, 0*1, 0(0\|1)*1, (0\|1)*1(0\|1)*, (micro)?( \|-)?(array\|chip)(s)? | ★★★ "which string matches" |
| Java Regex | classes Pattern (compile, matches, split), Matcher (find, start, end, group), PatternSyntaxException (unchecked); no public constructors | ★★★ MCQ |
| Character classes | [abc], [^abc], [a-zA-Z], union [a-d[m-p]], intersection [a-z&&[def]], subtraction [a-z&&[^bc]] | ★★ |
| Predefined | . \d \D \s \S \w = [a-zA-Z_0-9] \W | ★★★ |
| Quantifiers | ? * + {n} {n,} {n,m}; greedy X*, reluctant X*?, possessive X*+ | ★★★ |
| Boundaries | ^ $ \b \B \A \G \Z \z | ★★ |
| Examples | phone (\d){3}-(\d){3}-(\d){4}; postal [A-Za-z][0-9][A-Za-z]\s?[0-9][A-Za-z][0-9] | ★★ |
| Grammars | arithmetic expression grammar (E, I), simplified HTML grammar, terminals/non-terminals/start/productions | ★★ |
| Tools | grep, Lex, JFlex, jsoup (HTML to DOM), web crawler steps | ★ |

---

## Most likely hands-on (Level II) questions

1. Solve a recurrence with the Master theorem
2. Fill an LCS table and give the length
3. Fill an edit distance table and give the distance
4. MST weight with Prim or Kruskal, or the order edges are added
5. Dijkstra distances from a source
6. BFS or DFS visiting order
7. KMP failure function, or number of comparisons
8. Boyer-Moore last-occurrence table, or number of comparisons
9. Number of spanning trees (cycle or complete graph)
10. Which strings a regex matches, or write a small regex
