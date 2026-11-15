# Mid-Term 2 practice in Blooket style (Ch 5–8)

Same style as your old quizzes: a small case, 4 options, pick one. Answers with short working are at the **bottom**, so don't scroll down until you've finished a chapter.

---

## Ch 5: Advanced Design and Analysis

**5.1** T(n) = 4T(n/2) + n². Tightest bound?
A) Θ(n²) B) Θ(n² log n) C) Θ(n³) D) Θ(n log n)

**5.2** T(n) = 7T(n/2) + n². Tightest bound?
A) Θ(n²) B) Θ(n² log n) C) Θ(n^log₂7) D) Θ(n³)

**5.3** T(n) = 2T(n/2) + n log n (advanced form). Tightest bound?
A) Θ(n log n) B) Θ(n log² n) C) Θ(n²) D) Θ(n log log n)

**5.4** T(n) = T(n/2) + n. Tightest bound?
A) Θ(log n) B) Θ(n log n) C) Θ(n) D) Θ(n²)

**5.5** The recursive algorithm rF(k) computes Fibonacci. How many calls to rF are made in total for rF(6), counting the first call?
A) 13 B) 15 C) 25 D) 31

**5.6** DPFibonacci(10) fills the array A[0..10]. How many additions does it perform?
A) 8 B) 9 C) 10 D) 11

**5.7** What is the LCS length of X = ABCBDAB and Y = BDCABA?
A) 3 B) 4 C) 5 D) 6

**5.8** The LCS double loop runs on strings of length 8 and 7. Not counting row −1 and column −1, how many L[i,j] cells does it compute?
A) 15 B) 56 C) 72 D) 64

**5.9** What is the edit distance from SUNDAY to SATURDAY (substitution, insertion and deletion each cost 1)?
A) 2 B) 3 C) 4 D) 5

**5.10** A spellchecker compares a typed word of length m against n dictionary words, each of length at most m, using DP edit distance. Ignoring the ranking step, which is the tightest bound?
A) O(nm) B) O(n + m²) C) O(nm²) D) O(n²m)

---

## Ch 6: Graph Algorithms

Use this undirected weighted graph for **6.1 to 6.5**. Visit neighbours in alphabetical order.
```
A–B 7   A–C 3   B–C 1   B–D 2   C–D 8
C–E 6   D–E 4   D–F 5   E–F 9
```

**6.1** Kruskal processes the edges in sorted order. Which edge is the **first one rejected** because it would form a cycle?
A) A–B (7) B) C–E (6) C) C–D (8) D) D–F (5)

**6.2** What is the total weight of the MST?
A) 13 B) 15 C) 17 D) 19

**6.3** Prim starts at A. Which vertex is the **third** one added to the tree?
A) B B) C C) D D) E

**6.4** Dijkstra runs from A. What are the final values of d[B] and d[D]?
A) 7 and 9 B) 4 and 6 C) 4 and 11 D) 7 and 6

**6.5** BFS runs from A. What is d[F], the number of edges on the shortest path?
A) 2 B) 3 C) 4 D) 5

**6.6** How many spanning trees does a complete graph with 6 vertices have?
A) 36 B) 216 C) 1296 D) 7776

**6.7** An undirected graph has V = 6 and E = 9, stored as adjacency lists. How many list nodes are there in total?
A) 9 B) 15 C) 18 D) 36

**6.8** A graph has 12 vertices and 3 connected components. Running DFS with restarts gives a spanning forest. How many edges does that forest have?
A) 9 B) 11 C) 12 D) 15

**6.9** For a dense graph (E ≈ V²), which Prim implementation has the better bound?
A) Binary heap, O(E log V) B) Array, O(E + V²) C) Both are the same D) Neither works on dense graphs

**6.10** What is the running time of Dijkstra with a Fibonacci heap?
A) O(V²) B) O(E log E) C) O(E + V log V) D) O(V + E)

---

## Ch 7: Text Processing

**7.1** What is F(5), the last entry of the KMP failure function for P = AABAAA?
A) 1 B) 2 C) 3 D) 0

**7.2** P = ABCABD has F = [0,0,0,1,2,0]. KMP has matched ABCAB, and T[20] differs from P[5]. Which pair is compared next?
A) T[21] and P[0] B) T[20] and P[0] C) T[20] and P[2] D) T[21] and P[2]

**7.3** KMP searches T = XYXYXYZ for P = XYXYZ. How many character comparisons does it make in total?
A) 7 B) 8 C) 10 D) 12

**7.4** For the Boyer-Moore last-occurrence function of P = TOOTH (zero-based), what are L(T), L(O) and L(X)?
A) 0, 1, 0 B) 3, 2, −1 C) 3, 1, −1 D) 0, 2, 5

**7.5** In Boyer-Moore with P = TOOTH (m = 5), the first comparison is at j = 4 and the text character there is O. Using i ← i + m − min(j, 1 + L(O)), how much does i increase?
A) 1 B) 2 C) 3 D) 5

**7.6** Boyer-Moore searches T = TRUSTHARDTOOTHBRUSHES for P = TOOTH. How many character comparisons does it make until it finds the match?
A) 10 B) 14 C) 21 D) 25

**7.7** Brute force searches T = ABCABCABD for P = ABD. How many comparisons does it make until it finds the match?
A) 9 B) 11 C) 13 D) 21

**7.8** A standard trie stores {bear, bell, bid, bull, buy, sell, stock, stop}. How many nodes does it have, not counting the root?
A) 18 B) 21 C) 25 D) 30

**7.9** In the compact representation, S[2] = "sell". Which triple represents the node label "ell"?
A) (2, 0, 3) B) (2, 1, 3) C) (1, 2, 3) D) (2, 1, 4)

**7.10** In a ternary search trie (TST), how many links does each node have?
A) 2 B) 3 C) d (alphabet size) D) 26

---

## Ch 8: Languages

**8.1** Which string does **not** match the regular expression 0(0|1)*1?
A) 01 B) 001 C) 0110 D) 011

**8.2** How many binary strings of length 3 match (0|1)*1(0|1)*?
A) 3 B) 4 C) 7 D) 8

**8.3** How many **different strings** does (micro)?( |-)?(array|chip)(s)? match?
A) 8 B) 12 C) 16 D) 24

**8.4** How many characters does the Java class [a-z&&[^bc]] match?
A) 2 B) 23 C) 24 D) 26

**8.5** Repeated Matcher.find() with the greedy pattern a{2,3} runs on the text aaaaaaa (7 a's). How many matches does it find?
A) 2 B) 3 C) 4 D) 5

**8.6** Same text, but with the reluctant pattern a{2,3}?. How many matches?
A) 2 B) 3 C) 4 D) 7

**8.7** Which call returns **true**: Pattern.matches("(\\d){3}-(\\d){3}-(\\d){4}", s)?
A) "519 253 3000" B) "(519)253-3000" C) "519-253-3000" D) "+1-519-253-3000"

**8.8** Which string does **not** fully match [A-Za-z][0-9][A-Za-z]\s?[0-9][A-Za-z][0-9]?
A) N9B 3P4 B) n9b3p4 C) N9B3P4 D) N9B-3P4

**8.9** The language L = {0ⁿ1ⁿ | n ≥ 0} is best described as:
A) Regular, recognised by a finite automaton B) Context-free (not regular), recognised by a pushdown automaton C) Context-sensitive only D) Not recognisable

**8.10** Which production is **not** allowed in a context-sensitive grammar, where |α| ≤ |β|?
A) A → 0A B) AB → BA C) CB → DB D) AB → C

**8.11** Using the slide grammar (E → I | E+E | E*E | (E), and I → a | b | Ia | Ib | I0 | I1), which string is **not** derivable?
A) a1+b0 B) (ab)*b1 C) 1a+b D) a*(b+a0)

**8.12** What is the length of Pattern.compile(":").split("one:two:three:four")?
A) 3 B) 4 C) 5 D) 7

---
---

# Answers

## Ch 5
| Q | Ans | Why |
|---|---|---|
| 5.1 | **B** | a = 4, b = 2, d = 2, and log₂4 = 2 = d, so n² log n |
| 5.2 | **C** | log₂7 ≈ 2.81 > 2, so n^(log₂7) |
| 5.3 | **B** | a = 2, b = 2, k = 1, p = 1, so a = bᵏ and p > −1, giving n·log^(p+1) n = n log² n |
| 5.4 | **C** | log₂1 = 0 < d = 1, so n |
| 5.5 | **C** | calls(n) = 2F(n+1) − 1 = 2·13 − 1 = 25 |
| 5.6 | **B** | the loop runs i = 2..10, so 9 additions |
| 5.7 | **B** | 4, e.g. BCBA |
| 5.8 | **B** | 8 × 7 = 56 |
| 5.9 | **B** | insert A, insert T, substitute N with R |
| 5.10 | **C** | n words × O(m·m) each |

## Ch 6
| Q | Ans | Why |
|---|---|---|
| 6.1 | **B** | added in order: B–C 1, B–D 2, A–C 3, D–E 4, D–F 5. Then C–E 6 would close the cycle C-B-D-E |
| 6.2 | **B** | 1 + 2 + 3 + 4 + 5 = 15 |
| 6.3 | **A** | A, then C (3), then B (B–C 1) |
| 6.4 | **B** | d[B] = 3 + 1 = 4 (through C, the trap). d[D] = 4 + 2 = 6 |
| 6.5 | **B** | A → B → D → F |
| 6.6 | **C** | 6⁴ = 1296 |
| 6.7 | **C** | undirected, so each edge appears twice: 2E = 18 |
| 6.8 | **A** | V − (number of components) = 12 − 3 = 9 |
| 6.9 | **B** | E + V² = O(V²) beats V² log V |
| 6.10 | **C** | straight from the slide |

## Ch 7
| Q | Ans | Why |
|---|---|---|
| 7.1 | **B** | F = [0,1,0,1,2,2]. The suffix "AA" equals the prefix "AA" |
| 7.2 | **C** | j = F[4] = 2, and i stays at 20 |
| 7.3 | **B** | XYXY matches (4), then X≠Z ✗ so j = F[3] = 2, then XYZ matches (3). Total 4 + 1 + 3 = 8, and the match is at index 2 |
| 7.4 | **B** | the last T is at 3, the last O at 2, and X is not in P so −1 |
| 7.5 | **B** | 5 − min(4, 3) = 2 |
| 7.6 | **A** | 10 comparisons, match at index 9 |
| 7.7 | **C** | 13 comparisons, match at index 6 |
| 7.8 | **B** | b, be, bea, bear, bel, bell, bi, bid, bu, bul, bull, buy, s, se, sel, sell, st, sto, stoc, stock, stop = 21 |
| 7.9 | **B** | S[2][1..3] = "ell" |
| 7.10 | **B** | less than, equal, greater than |

## Ch 8
| Q | Ans | Why |
|---|---|---|
| 8.1 | **C** | 0110 ends in 0 |
| 8.2 | **C** | every string except 000: 8 − 1 = 7 |
| 8.3 | **D** | 2 × 3 × 2 × 2 = 24 (the "( \|-)?" part has 3 choices: nothing, space, dash) |
| 8.4 | **C** | 26 − 2 = 24 |
| 8.5 | **A** | greedy takes aaa, then aaa, and the last a is too short |
| 8.6 | **B** | reluctant takes aa, aa, aa |
| 8.7 | **C** | matches() needs the whole string to fit the pattern |
| 8.8 | **D** | a dash isn't whitespace |
| 8.9 | **B** | classic CFL, A → 0A1 \| ε |
| 8.10 | **D** | the right side is shorter than the left |
| 8.11 | **C** | identifiers must start with a or b |
| 8.12 | **B** | one, two, three, four |
