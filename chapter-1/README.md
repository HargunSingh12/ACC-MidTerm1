# Chapter 1: Algorithm Analysis

COMP 8547 Advanced Computing Concepts, Mid-Term I (Friday 23 October 2026). This page covers **only Chapter 1**. Everything here comes from the Chapter 1 slides. The full four-chapter guide is in [../study-guide.md](../study-guide.md).

**On this page**
1. [What an algorithm is](#1-what-an-algorithm-is)
2. [Why analyse, and how to compare](#2-why-analyse-and-how-to-compare)
3. [Experimental vs theoretical analysis](#3-experimental-vs-theoretical-analysis)
4. [Primitive operations and counting](#4-primitive-operations-and-counting)
5. [Growth rates](#5-growth-rates)
6. [Best, worst and average case](#6-best-worst-and-average-case)
7. [Asymptotic notation](#7-asymptotic-notation)
8. [Finding c and n0](#8-finding-c-and-n0)
9. [Rules for analysing code](#9-rules-for-analysing-code)
10. [Slide code examples](#10-slide-code-examples)
11. [Case studies](#11-case-studies)
12. [Java (short)](#12-java-short)
13. [Slide exercises with answers](#13-slide-exercises-with-answers)
14. [Last-minute checklist](#14-last-minute-checklist)

---

## 1. What an algorithm is

> An algorithm is a sequence of step-by-step, unambiguous instructions that solves a problem in a finite amount of time.

The slides illustrate this with making an omelette (get the pan, check for oil, buy oil or stop, turn on the stove, …).

Three properties:
- **Correctness:** gives the correct output for every input.
- **Performance:** measured by the resources it uses (time and space).
- **End:** finishes in a finite amount of time.

A **problem** is what has to be solved. An **algorithm** is one way to solve it. One problem can have many algorithms with different complexities. For example, sorting can be done with insertion, selection or quick sort, and searching a sorted array with linear search (O(n)) or binary search (O(log n)).

## 2. Why analyse, and how to compare

Algorithm analysis tells you which algorithm is most efficient in **time and space**. The slides compare it to choosing between flight, bus, train or bicycle to get from city A to city B.

**Running-time analysis** studies how processing time grows as the **input size** grows. Input size depends on the problem:
- the size of an array
- the degree of a polynomial
- the number of elements in a matrix
- the number of bits in the input
- the vertices and edges of a graph

How to compare algorithms:

| Measure | Good? | Why |
|---|---|---|
| Execution time | No | It depends on the specific computer |
| Number of statements | No | It depends on the language and the programmer's style |
| **Running time as a function f(n) of input size** | **Yes** | It is independent of machine and style |

## 3. Experimental vs theoretical analysis

**Experimental:** implement the algorithm, run it on inputs of different sizes, record CPU time and plot it.
Limitations:
- it depends on the hardware and the language
- you must implement and debug the program first
- it only covers the inputs you tried

**Theoretical (the framework used in this course):**
1. State the problem.
2. Write the algorithm in **pseudocode**.
3. Count the **primitive operations** to get T(n).
4. Find the **asymptotic notation** for T(n).
5. Compare it with other algorithms.

Advantages: it uses a high-level description, gives running time as a function of n, covers **all** inputs, and is independent of hardware and software.

**Pseudocode conventions:** `if … then … [else …]`, `while … do`, `repeat … until`, `for … do`; indentation replaces braces; `←` is assignment and `=` is equality testing; methods are declared as `Algorithm name(args)` with Input/Output lines.

## 4. Primitive operations and counting

A primitive operation is a basic computation that takes **constant time** in the RAM model:
- evaluating an expression
- assigning a value to a variable
- indexing into an array
- calling a method
- returning from a method

**arrayMax** (worst case):

| Line | # operations |
|---|---|
| `currentMax ← A[0]` | 2 |
| `for i ← 1 to n − 1 do` | 2n |
| `if A[i] > currentMax then` | 2(n − 1) |
| `currentMax ← A[i]` | 2(n − 1) |
| `{ increment counter i }` | 2(n − 1) |
| `return currentMax` | 1 |
| **Total** | **T(n) = 8n − 3** → O(n) |

The exact count does not matter much, because constants disappear in Big-O.

## 5. Growth rates

**Rate of growth** is how fast the running time increases with the input size. The slides use the analogy of buying a car and a bicycle: total cost ≈ the cost of the car. In the same way, drop the low-order terms:

n⁴ + 2n² + 100n + 500 ≈ **n⁴**

Common rates, slowest to fastest:

| Name | Function |
|---|---|
| Constant | 1 |
| Logarithmic | log n |
| Linear | n |
| N-log-N | n log n |
| Quadratic | n² |
| Cubic | n³ |
| Exponential | 2ⁿ |

On a **log-log chart**, the slope of the line is the growth rate (this does not hold for exponential functions).

## 6. Best, worst and average case

- **Worst case:** the input that takes the longest.
- **Best case:** the input that runs fastest.
- **Average case:** the average over all inputs, i.e. the expected value of T(n).

Slide example: linear search for 7.

```
i ← 0
while i < n and A[i] != 7 do    worst: n    best: 1
    i ← i + 1                   worst: n    best: 0
```
- Worst-case input `3 1 4 2 3 2 1 8` (7 is not there) → **O(n)**
- Best-case input `7 1 5 4 8 2 1 9` (7 comes first) → **O(1)**

For loops, take the **maximum** iterations for the worst case and the **minimum** for the best case.

## 7. Asymptotic notation

| Name | Notation | Bound | Slides' note |
|---|---|---|---|
| Big-Oh | O(g) | upper, tight | the most common notation for an algorithm's complexity |
| Big-Theta | Θ(g) | upper and lower, tight | the most accurate notation |
| Big-Omega | Ω(g) | lower, tight | mostly for lower bounds of *problems* (e.g. sorting) |
| Little-oh | o(g) | upper, loose | when a tight upper bound is hard to get |
| Little-omega | ω(g) | lower, loose | when a tight lower bound is hard to get |

The slides also pair them with cases. **Expect an MCQ worded this way:**
- **Big-O → worst case** (upper boundary)
- **Big-Ω → best case** (lower boundary)
- **Big-Θ → average case** ("average" boundary)

### Definitions

- **Big-Oh:** f(n) is O(g(n)) if there are positive constants **c** and **n0** such that **f(n) ≤ c·g(n) for all n ≥ n0**. So f grows no faster than g.
- **Big-Omega:** f(n) is Ω(g(n)) if there are c > 0 and n0 ≥ 1 such that **f(n) ≥ c·g(n) for n ≥ n0**. Example: 3n³ − 2n + 1 is Ω(n³).
- **Big-Theta:** f(n) is Θ(g(n)) if there are c′ > 0, c″ > 0 and n0 ≥ 1 such that **c′·g(n) ≤ f(n) ≤ c″·g(n) for n ≥ n0**. Example: 5n log n − 2n is Θ(n log n).
- **Little-oh:** f(n) is o(g(n)) if **for any** c > 0 there is n0 > 0 with **f(n) < c·g(n)** for n ≥ n0. Example: 3n² − 2n + 1 is o(n³), but **not** o(n²).
- **Little-omega:** f(n) is ω(g(n)) if **for any** c > 0 there is n0 > 0 with **f(n) > c·g(n)** for n ≥ n0. Example: 3n² − 2n + 1 is ω(n), but **not** ω(n²).

**The key difference:** for O and Ω the inequality must hold for **some** constant c. For o and ω it must hold for **every** constant c > 0.

### Important axioms
- f is O(g) **and** Ω(g) ⇔ f is Θ(g). Example: 5n² is O(n²) and Ω(n²), so 5n² is Θ(n²).
- f is o(g) ⇔ g is ω(f).

### Big-Oh rules
- "f(n) is O(g(n))" means the growth rate of f is no more than the growth rate of g.
- O(g(n)) is a **set** (class) of functions.
- A polynomial of degree d is **O(nᵈ)**; with d = 0 it is O(1). Example: n² + 3n − 1 is O(n²).
- Use the **simplest** expression: say 2n + 3 is O(n), not O(4n) or O(3n + 1).
- Use the **smallest** class: say 2n is O(n), not O(n²) or O(n³).
- **Linearity:** O(f) + O(g) = O(f + g) = O(max{f, g}). Example: O(n) + O(n²) = O(n²).

## 8. Finding c and n0

This is a Level II short-answer question on the exam ("Find upper bound for f(n) = 2n + 10").

**Method:** write f(n) ≤ c·g(n), rearrange to isolate n, pick a c, then read off n0.

**Example (slides):** f(n) = 2n + 10, g(n) = n.
- 2n + 10 ≤ cn
- (c − 2)n ≥ 10
- n ≥ 10/(c − 2)
- Pick **c = 3**, so **n0 = 10**. Then 2n + 10 ≤ 3n for all n ≥ 10, and f(n) is **O(n)**.

**Example:** f(n) = 3n² + 5n + 2 is O(n²).
- Quick way: for n ≥ 1, 3n² + 5n + 2 ≤ 3n² + 5n² + 2n² = 10n², so **c = 10, n0 = 1**.
- Tighter: with c = 4 you need n² − 5n − 2 ≥ 0, which holds from **n0 = 6**.

**Disproving:** 2n² + 3 is **not** O(n). 2n² + 3 ≤ cn would need 2n ≤ c for all large n, and no constant c is that big.

## 9. Rules for analysing code

1. **Loops:** body time × number of iterations.
   `for (i=1; i<=n; i++) m = m + 2;` → c·n = **O(n)**
2. **Nested loops:** analyse from the inside out and multiply the loop sizes.
   two nested loops of n → c·n·n = **O(n²)**
3. **Consecutive statements:** add them, and the largest term wins.
   `x = x + 1;` then a loop of n, then a double loop of n → c₀ + c₁n + c₂n² = **O(n²)**
4. **If-then-else:** the test plus the **larger** of the two branches.
   Constant `then` branch, `else` branch is a loop of n → **O(n)**
5. **Logarithmic:** constant time to cut the problem by a fraction (usually ½).
   `for (i=1; i<=n;) i = i*2;` runs k times where 2ᵏ = n, so k = log n → **O(log n)**.
   `for (i=n; i>=1;) i = i/2;` is also **O(log n)**.
   Binary search works the same way: look at the middle of a dictionary and keep only the half the word is in.

**Two independent inputs:** a loop over N followed by a loop over M → **O(N + M)**. You cannot say which term leads.

## 10. Slide code examples

**Example 1**
```c
for (i = n/2; i <= n; i++)              // n/2 times
  for (j = 1; j + n/2 <= n; j = j+1)    // n/2 times
    for (k = 1; k <= n; k = k*2)        // log n times
      count++;
```
→ **O(n² log n)**

**Example 2**
```c
for (i = n/2; i <= n; i++)              // n/2 times
  for (j = 1; j <= n; j = 2*j)          // log n times
    for (k = 1; k <= n; k = k*2)        // log n times
      count++;
```
→ **O(n log² n)**

**Example 3**
```c
if (n == 1) return;                     // constant
for (int i = 1; i <= n; i++)            // n times
  for (int j = 1; j <= n; j++) {        // runs once: break
    printf("*");
    break;
  }
```
→ **O(n)**. The inner loop is bounded by n, but the `break` stops it after one pass.

## 11. Case studies

### Case study 1: search in a sorted array (a map)

`S = 8 12 19 22 23 34 41 48` (indices 0–7)

| | Linear search | Binary search |
|---|---|---|
| Idea | scan one by one until k is found | compare with the middle, recurse into the left or right half |
| Worst-case T(n) | 3n + 4 | T(n) = T(n/2) + 1 |
| Big-O | **O(n)** | **O(log n)** |

```
Algorithm binarySearch(S, k, low, high):
  if low > high then return null
  mid ← (low + high) / 2
  e ← S[mid]
  if k = e.getKey() then return e
  else if k < e.getKey() then return binarySearch(S, k, low, mid−1)
  else return binarySearch(S, k, mid+1, high)
```
Same problem, two algorithms, different running times.

### Case study 2: prefix averages

The i-th prefix average is A[i] = (S[0] + … + S[i]) / (i + 1). It is used in financial analysis, for example running averages of prices.

`S = 21 23 25 31 20 18 16` → `A = 21 22 23 25 24 23 22`

| | quadPrefixAve | linearPrefixAve |
|---|---|---|
| Idea | for each i, re-add S[0..i] with an inner loop | keep a running sum s |
| Inner work | 1 + 2 + … + (n − 1) = n(n − 1)/2 | one addition per i |
| T(n) | 2n + 2(n − 1) + 2·n(n − 1)/2 + 1 | about 4n |
| Big-O | **O(n²)** | **O(n)** |

```
Algorithm linearPrefixAve(S, n)
  A ← new array of n integers
  s ← 0
  for i ← 0 to n − 1 do
    s ← s + S[i]
    A[i] ← s / (i + 1)
  return A
```

### Case study 3: maximum contiguous subsequence sum (MCSS)

Given integers A₁ … Aₙ (possibly negative), find the largest sum of consecutive elements. **If all are negative, MCSS = 0.**

Slide examples:
- −3, 10, −2, 11, −5, −2, 3 → **19** (10 − 2 + 11)
- −7, −10, −1, −3 → **0**
- 12, −5, −6, −4, 3 → **12**

| Algorithm | Idea | Time |
|---|---|---|
| Cubic | try every (i, j) and add A[i..j] with a third loop | T(n) = (n³ + 3n² + 2n)/6 + c → **O(n³)** |
| Quadratic | for each i, extend j and keep a running sum | ~n(n − 1)/2 → **O(n²)** |
| Divide and conquer | MCSS is in the left half, the right half, or spans both | T(n) = 2T(n/2) + n, T(1) = 1 → **O(n log n)** |
| Linear | one pass; reset the running sum to 0 when it goes negative | **O(n)** |

**Divide and conquer, step by step**
1. Split the sequence into two halves.
2. Recursively find the MCSS of each half.
3. **Max left border sum:** the best sum ending at the last element of the left half, going left.
4. **Max right border sum:** the best sum starting at the first element of the right half, going right.
5. Spanning sum = left border + right border. The answer is the max of the three.

Slide example: A = −3, 10, −2, 11 | −1, 2, −3
- Left half MCSS = 19. Right half MCSS = 2.
- Left border sum = 19 (11, −2, 10). Right border sum = 1 (−1, 2).
- Spanning sum = 20, so **MCSS = 20** (10, −2, 11, −1, 2).

**Linear algorithm**
```
Algorithm linearMCSS(A, n)
  maxS ← 0; curS ← 0
  for j ← 0 to n − 1 do
    curS ← curS + A[j]
    if curS > maxS then maxS ← curS
    else if curS < 0 then curS ← 0
  return maxS
```
The tricky parts: no MCSS starts or ends with a negative number. The algorithm finds only the **value** of the MCSS; to get the actual subsequence you need at least divide and conquer.

Trace on 3, 4, −7, 3, 6, −3, 2, 8, −1: curS = 3, 7, 0, 3, 9, 6, 8, 16, 15 → **MCSS = 16** (3, 6, −3, 2, 8).

## 12. Java (short)

Labs use **Java** on the JVM ("write once, run anywhere"). The slides give these reasons:
1. It is widely used (over 9 million developers).
2. It is platform independent.
3. It is object oriented, so code is modular and scalable.
4. It is robust and secure, with strong memory management.
5. It has a huge community and ecosystem of libraries and frameworks.
6. It is used in enterprise applications (financial services, Android apps).

Generics: `public class MyClass<AnyType>`, generic static methods `public static <AnyType> boolean find(AnyType[] a, AnyType x)`. Generics have restrictions (e.g. no primitive types).

**Java SE** (Standard Edition) is used for the course implementations. **Java EE** (Enterprise Edition) is developed through the Java Community Process. It is a rich, widely used, scalable, low-risk platform with better HTML5 support and support for the latest web frameworks. Course IDE: **Eclipse**.

## 13. Slide exercises with answers

**Ex 1. Sort by growth rate:** 12n², 3n, 0.5 log n, n log n, 2n³
→ 0.5 log n < 3n < n log n < 12n² < 2n³

**Ex 2.** A uses 20 n log n operations and B uses 2n². When is A faster?
→ 20 n log n < 2n² ⇔ 10 log₂ n < n. This first holds at **n0 = 59** (10 · log₂ 59 ≈ 58.8 < 59, while at 58 it is 58.6 > 58). For n = 10,000 use **A**.

**Ex 3.** For f(n) = 2n² + 3:

| Claim | Answer | Reason |
|---|---|---|
| O(n) | **False** | n² outgrows n |
| O(n¹⁰) | **True** | an upper bound, just not tight |
| Ω(1) | **True** | f ≥ 1 |
| Θ(n²) | **True** | between 2n² and 5n² for n ≥ 1 |
| o(n^(9/4)) | **True** | n²/n^2.25 → 0 |
| ω(√n) | **True** | n²/√n → ∞ |
| o(n²) | **False** | the ratio → 2, not 0 |

**Ex 4.** MCSS of 3, 4, −7, 3, 6, −3, 2, 8, −1 → **16** with every algorithm (see the trace in section 11).

**Ex 5.** Worst case of linearMCSS is **O(n)** (one loop, constant work inside). quadraticMCSS: the inner loop runs n − i times, Σ = n(n + 1)/2 → **O(n²)**. Both are also Θ of the same function, since their loops always run in full.

**Ex 7. True or false**
- (a) f is O(g) ⇒ f is Ω(g): **False** (n is O(n²) but not Ω(n²))
- (b) f is O(g) ⇒ g is Ω(f): **True**
- (c) f is O(g) and Ω(g) ⇒ f is Θ(g): **True**
- (d) f is O(g) and g is O(f) ⇒ f is Θ(g): **True**
- (e) f is o(g) ⇒ f is O(g): **True**
- (f) f is Θ(g) ⇒ f is o(g): **False**

**Ex 12.** An algorithm whose best and worst cases differ by more than a constant:
→ **linear search**: O(1) when the key is first, O(n) when it is missing.

**Ex 14.** Main O rules: drop constants and lower-order terms, use the simplest and smallest class, and O(f) + O(g) = O(max(f, g)). The same rules apply to Ω and Θ. For Ω you keep the largest lower bound instead of the smallest upper bound.

**Ex 15.** Problem vs algorithm: the problem is *what* to solve; the algorithm is *how*. For example, searching a sorted array is one problem. Linear search solves it in O(n) and binary search in O(log n).

## 14. Last-minute checklist

- [ ] Order 1, log n, n, n log n, n², n³, 2ⁿ without thinking
- [ ] Write the formal definitions of O, Ω, Θ, o, ω, and know "some c" vs "every c"
- [ ] Know the slides' pairing: O ↔ worst, Ω ↔ best, Θ ↔ average
- [ ] Find c and n0 for a linear or quadratic f(n) and show the inequality
- [ ] Analyse loops: halving or doubling → log n, nested → multiply, sequential → add, a `break` → constant
- [ ] arrayMax = 8n − 3; linear search = 3n + 4; binary search T(n) = T(n/2) + 1
- [ ] Prefix averages O(n²) vs O(n); MCSS O(n³) / O(n²) / O(n log n) / O(n)
- [ ] Trace linear MCSS and the divide-and-conquer border sums by hand
- [ ] Remember that MCSS = 0 when every number is negative

Practice: in [../practice-questions.md](../practice-questions.md) the Chapter 1 questions are A1, A12, A13, A16, A17, C10, C11, C18, C21–C24, D1–D4, D22, D24–D27 and D47.
