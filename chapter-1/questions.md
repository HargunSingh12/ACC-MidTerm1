# Chapter 1: Algorithm Analysis, Question Bank

Every question type from the Mid-Term I format, for **Chapter 1 only**. The answer key is at the bottom. Notes for this chapter are in [README.md](README.md).

| Part | Exam section | Questions |
|---|---|---|
| A | MCQ Level I (simple) | A1–A18 |
| B | MCQ Level II (scenarios) | B1–B13 |
| C | Short answer Level I (fill in) | C1–C22 |
| D | Short answer Level II (hands-on) | D1–D22 |

Logs are base 2 unless stated.

---

## Part A. MCQ Level I

**A1.** An algorithm is: (a) any computer program (b) a step-by-step, unambiguous procedure that solves a problem in finite time (c) a data structure (d) a programming language

**A2.** Which is **not** one of the slides' algorithm properties? (a) correctness (b) performance (c) finishes in finite time (d) uses recursion

**A3.** Why is measured execution time a poor way to compare algorithms? (a) it is always zero (b) it depends on the specific computer (c) it ignores input (d) it counts statements

**A4.** Why is the number of statements a poor measure? (a) it varies with the language and the programmer's style (b) it is hard to count (c) it is always n (d) it ignores loops

**A5.** Which is **not** a primitive (constant-time) operation? (a) assigning a variable (b) indexing an array (c) returning from a method (d) sorting an array

**A6.** On a log-log chart, the slope of a function's line corresponds to its: (a) constant factor (b) growth rate (c) best case (d) memory use

**A7.** n⁴ + 2n² + 100n + 500 is approximately: (a) 500 (b) 100n (c) n⁴ (d) 2n²

**A8.** Big-Theta gives: (a) only an upper bound (b) only a lower bound (c) a tight upper and lower bound (d) a loose upper bound

**A9.** Which notation is mostly used for lower bounds of *problems* (e.g. sorting)? (a) O (b) Ω (c) o (d) Θ

**A10.** Little-oh is used when: (a) a tight upper bound is hard to obtain (b) the function is constant (c) the best case is needed (d) n is small

**A11.** O(n) + O(n²) equals: (a) O(n) (b) O(n³) (c) O(n²) (d) O(n + 1)

**A12.** We write "2n is O(n)" rather than "O(n²)" because we use: (a) the largest class (b) the smallest possible class (c) the slowest class (d) any class

**A13.** We write "2n + 3 is O(n)" rather than "O(3n + 1)" because we use: (a) the simplest expression (b) the exact count (c) the worst case (d) Big-Omega

**A14.** The average-case running time can be seen as: (a) the minimum of T(n) (b) the expected value of T(n) (c) the maximum of T(n) (d) T(1)

**A15.** In the slides, Big-Omega is associated with which case? (a) worst (b) average (c) best (d) none

**A16.** Binary search requires that the array is: (a) unsorted (b) sorted (c) of even length (d) stored in a linked list

**A17.** If every number in the sequence is negative, the MCSS is: (a) the largest number (b) the smallest number (c) 0 (d) undefined

**A18.** The course implementations use: (a) Java EE (b) Java SE (c) JavaScript (d) Kotlin

---

## Part B. MCQ Level II (scenarios)

**B1.** Two students time the same algorithm on different laptops and get very different numbers. What should they use to compare algorithms fairly? (a) the faster laptop (b) theoretical analysis: count primitive operations and use asymptotic notation (c) the average of both times (d) lines of code

**B2.** A phone directory holds 10 million names in sorted order. You need to look up one name. Choose: (a) linear search (b) binary search (c) sort it again first (d) check every second name

**B3.** You have an **unsorted** list of 1,000 items and need to search it **once**. Best choice? (a) sort it, then binary search (b) linear search (c) build a tree first (d) binary search directly

**B4.** A trading app must show, for each new day, the average price of all days so far. Which approach scales? (a) recompute the sum of all days every time (b) keep a running sum (c) sort the prices (d) store only today's price

**B5.** Given 5 million daily gains and losses, find the largest total gain over any consecutive run of days (value only), as fast as possible. Use: (a) cubic MCSS (b) quadratic MCSS (c) divide-and-conquer MCSS (d) linear MCSS

**B6.** Algorithm A takes 20·n·log n steps and B takes 2n² steps. Your inputs always have **n = 30**. Which is faster? (a) A (b) B (c) the same (d) cannot tell

**B7.** Same algorithms as B6, but now inputs have **n = 10 million**. Which is faster? (a) A (b) B (c) the same (d) cannot tell

**B8.** A developer says her method is O(n) "because it has one loop", but each iteration calls binary search on a sorted array of size n. The real complexity is: (a) O(n) (b) O(log n) (c) O(n log n) (d) O(n²)

**B9.** A program processes a list of N customers and then, separately, a list of M products. Its complexity is: (a) O(N·M) (b) O(N + M) (c) O(max(N, M)²) (d) O(1)

**B10.** When you double the input size, the running time roughly **quadruples**. The algorithm is most likely: (a) O(log n) (b) O(n) (c) O(n²) (d) O(2ⁿ)

**B11.** When you double the input size, the running time grows by only a **constant amount**. The algorithm is most likely: (a) O(log n) (b) O(n) (c) O(n log n) (d) O(n²)

**B12.** A search stops as soon as it finds the key. Your manager wants a guarantee that holds for **every** input. You should report the: (a) best case (b) worst case (c) average for one test (d) time on your laptop

**B13.** You want to state that **no** algorithm for a problem can be faster than some function. Which notation do you use? (a) O (b) Ω (c) o (d) none

---

## Part C. Short answer Level I

C1. f(n) is O(g(n)) if there exist positive constants ______ and ______ such that f(n) ≤ c·g(n) for all n ≥ n0.
C2. Worst-case number of primitive operations of arrayMax: T(n) = ______.
C3. Worst-case running time of linear search on a sorted array: T(n) = ______, which is ______.
C4. The recurrence for binary search is T(n) = ______, which is ______.
C5. `for (i = n; i >= 1; i = i / 2)` runs in ______.
C6. Two nested loops, each running n times with a constant body, take ______.
C7. Running time of quadPrefixAve: ______.
C8. Running time of linearPrefixAve: T(n) = ______, which is ______.
C9. The divide-and-conquer MCSS recurrence is T(n) = ______ with T(1) = 1, which gives ______.
C10. The cubic MCSS algorithm runs in ______; the quadratic one in ______; the linear one in ______.
C11. A polynomial of degree d is O(______). If d = 0, it is O(______).
C12. 5n log n − 2n is Θ(______).
C13. 3n³ − 2n + 1 is Ω(______).
C14. f(n) is o(g(n)) if and only if g(n) is ______(f(n)).
C15. f(n) is O(g(n)) and Ω(g(n)) if and only if f(n) is ______(g(n)).
C16. Slide Example 1 (loops of n/2, n/2 and doubling k) runs in ______.
C17. Slide Example 2 (loops of n/2, doubling j and doubling k) runs in ______.
C18. Slide Example 3 (inner loop with a `break`) runs in ______.
C19. The prefix averages of S = 21 23 25 31 20 18 16 are ______.
C20. The MCSS of −3, 10, −2, 11, −5, −2, 3 is ______.
C21. For o and ω the inequality must hold for ______ constant c > 0; for O and Ω it must hold for ______ constant c > 0.
C22. Java programs run on the ______, which makes them "write once, run anywhere".

---

## Part D. Short answer Level II (hands-on)

**D1.** Find an upper bound for f(n) = 2n + 10. Give c and n0. *(exam example)*

**D2.** Show 7n − 2 is O(n). Give c and n0.

**D3.** Show 3n³ + 20n² + 5 is O(n³). Give c and n0.

**D4.** Show 3 log n + 5 is O(log n). Give c and n0.

**D5.** Show 2ⁿ⁺² is O(2ⁿ). Give c and n0.

**D6.** Show 5n log n − 2n is Θ(n log n). Give c′, c″ and n0.

**D7.** Prove that n² is **not** O(n).

**D8.** Sort by growth rate, slowest first: n², 2ⁿ, n log n, 100, log n, n³, √n, n, 10 n log n.

**D9.** True or false, with a reason: (a) n log n is O(n²) (b) n² is O(n log n) (c) 2ⁿ is O(3ⁿ) (d) 3ⁿ is O(2ⁿ) (e) log₂ n is Θ(log₁₀ n) (f) 3n² − 2n + 1 is o(n³) (g) 3n² − 2n + 1 is ω(n²)

**D10.** Simplify: (a) O(n² + n log n + 1000) (b) O(3n + 2 log n) (c) O(n) + O(n log n) + O(1) (d) O(50)

**D11.** Using the slides' counts, how many primitive operations does arrayMax perform in its **best** case (when A[0] is already the maximum)?

**D12.** Give the Big-O of each fragment:
```java
// (a)
for (i = 1; i <= n; i++)
  for (j = 1; j <= n; j += i) count++;
// (b)
for (i = 1; i <= n; i *= 2)
  for (j = 1; j <= i; j++) count++;
// (c)
for (i = 0; i < n; i++)
  for (j = 0; j < n; j++)
    for (k = 0; k < 100; k++) count++;
// (d)
int i = n;
while (i > 0) {
  for (j = 0; j < n; j++) count++;
  i = i / 2;
}
// (e)
for (i = 1; i <= n; i++)
  for (j = 1; j <= i; j++)
    for (k = 1; k <= j; k++) count++;
// (f)
if (n % 2 == 0)
  for (i = 0; i < n; i++) count++;
else
  for (i = 0; i < n; i++)
    for (j = 0; j < n; j++) count++;
```

**D13.** Give the running time of each recursive method:
```java
void f(int n) { if (n <= 1) return; f(n / 2); }
void g(int n) {
  if (n <= 1) return;
  for (int i = 0; i < n; i++) count++;
  g(n / 2); g(n / 2);
}
```

**D14.** Algorithm A uses 8·n·log n operations and B uses 2n². From which n0 is A strictly faster?

**D15.** Algorithm A uses 100n operations and B uses n². When is A faster? Which would you pick for n = 50 and for n = 5,000?

**D16.** Linear search for 5 in A = 2 9 5 1 7. How many loop tests `A[i] != 5` are made? Give a best-case and a worst-case input of size 5 for searching 5.

**D17.** Binary search on S = 8 12 19 22 23 34 41 48 (indices 0–7, mid = ⌊(low + high)/2⌋). List the keys compared when searching for 34, then for 20.

**D18.** Compute the prefix averages of (a) S = 10 20 30 40 50 and (b) S = 4 8 6 2 10.

**D19.** Trace linearMCSS (give curS after each element and the final maxS) on (a) 5, −9, 6, −2, 3, (b) −2, 11, −4, 13, −5, −2.

**D20.** Divide-and-conquer MCSS on A = 4, −3, 5, −2 | −1, 2, 6, −2. Give each half's MCSS, the max left-border sum, the max right-border sum and the final answer.

**D21.** Find the MCSS of 1, −3, 4, −1, 2, 1, −5, 4 and of 2, −1, 2, −1, 2.

**D22.** Give an algorithm whose best and worst cases differ by more than a constant factor, with both running times.

---
---

# Answer key

## Part A
A1 b · A2 d · A3 b · A4 a · A5 d · A6 b · A7 c · A8 c · A9 b · A10 a · A11 c · A12 b · A13 a · A14 b · A15 c · A16 b · A17 c · A18 b

## Part B
- B1 **b**: the theoretical analysis is independent of hardware and language.
- B2 **b**: O(log n), about 24 comparisons for 10 million names.
- B3 **b**: one O(n) scan. Sorting first costs O(n log n), which is more than the search saves.
- B4 **b**: linearPrefixAve is O(n) in total (O(1) per new day); recomputing is O(n²).
- B5 **d**: linear MCSS is O(n).
- B6 **b**: at n = 30, A ≈ 20 · 30 · 4.91 ≈ 2,944 and B = 2 · 900 = 1,800. Small n, so constants matter.
- B7 **a**: for large n, n log n beats n² (A wins for every n ≥ 59).
- B8 **c**: n iterations × O(log n) each = O(n log n).
- B9 **b**: independent consecutive loops add up.
- B10 **c**: (2n)² = 4n².
- B11 **a**: log(2n) = log n + 1.
- B12 **b**: Big-O / worst case is the guarantee for every input.
- B13 **b**: Ω is a lower bound, mostly used for problems.

## Part C
C1 c, n0 · C2 8n − 3 · C3 3n + 4, O(n) · C4 T(n/2) + 1, O(log n) · C5 O(log n) · C6 O(n²) · C7 O(n²) · C8 4n, O(n) · C9 2T(n/2) + n, O(n log n) · C10 O(n³); O(n²); O(n) · C11 nᵈ; 1 · C12 n log n · C13 n³ · C14 ω · C15 Θ · C16 O(n² log n) · C17 O(n log² n) · C18 O(n) · C19 21 22 23 25 24 23 22 · C20 19 · C21 every; some (at least one) · C22 Java Virtual Machine (JVM)

## Part D

**D1.** 2n + 10 ≤ cn ⇔ (c − 2)n ≥ 10. With **c = 3, n0 = 10**: 2n + 10 ≤ 3n for every n ≥ 10. So **O(n)**.

**D2.** 7n − 2 ≤ 7n for all n ≥ 1 → **c = 7, n0 = 1**.

**D3.** With c = 4 you need n³ ≥ 20n² + 5. At n = 20: 8,000 < 8,005 (fails). At n = 21: 9,261 ≥ 8,825 (holds) → **c = 4, n0 = 21**. Simpler option: for n ≥ 1, 3n³ + 20n² + 5 ≤ 3n³ + 20n³ + 5n³ = 28n³ → **c = 28, n0 = 1**.

**D4.** For n ≥ 2, log n ≥ 1, so 5 ≤ 5 log n. Then 3 log n + 5 ≤ 8 log n → **c = 8, n0 = 2**. (n0 = 1 fails because log 1 = 0.)

**D5.** 2ⁿ⁺² = 4 · 2ⁿ, so 2ⁿ⁺² ≤ 4 · 2ⁿ → **c = 4, n0 = 1**.

**D6.** Upper: 5n log n − 2n ≤ 5n log n → c″ = 5. Lower: c′ n log n ≤ 5n log n − 2n ⇔ (5 − c′) log n ≥ 2. With c′ = 3 that is log n ≥ 1, i.e. n ≥ 2 → **c′ = 3, c″ = 5, n0 = 2**.

**D7.** Suppose n² ≤ cn for all n ≥ n0. Dividing by n gives n ≤ c for all n ≥ n0, which is false for n > c. So no constants exist, and **n² is not O(n)**.

**D8.** 100 < log n < √n < n < n log n = 10 n log n (same class) < n² < n³ < 2ⁿ.

**D9.**
- (a) **T**, n log n ≤ n² for n ≥ 1.
- (b) **F**, n²/(n log n) = n/log n → ∞.
- (c) **T**, 2ⁿ ≤ 3ⁿ.
- (d) **F**, (3/2)ⁿ → ∞.
- (e) **T**, log₂ n = log₁₀ n / log₁₀ 2; changing the base is a constant factor.
- (f) **T**, the ratio to n³ → 0.
- (g) **F**, the ratio to n² → 3, not ∞. It is ω(n).

**D10.** (a) **O(n²)** (b) **O(n)** (c) **O(n log n)** (d) **O(1)**

**D11.** Best case skips `currentMax ← A[i]` every time: 2 + 2n + 2(n − 1) + 2(n − 1) + 1 = **6n − 1**. (Worst case is 8n − 3.) Both are O(n).

**D12.**
- (a) n/1 + n/2 + n/3 + … + n/n = n(1 + ½ + … + 1/n) ≈ n ln n → **O(n log n)**
- (b) 1 + 2 + 4 + … + n ≤ 2n → **O(n)**
- (c) 100 · n · n → **O(n²)** (the 100 is a constant)
- (d) log n passes × n each → **O(n log n)**
- (e) Σ i(i + 1)/2 ≈ n³/6 → **O(n³)**
- (f) the worst case takes the larger branch → **O(n²)**

**D13.** f: T(n) = T(n/2) + 1 → **O(log n)** (like binary search). g: T(n) = 2T(n/2) + n → **O(n log n)** (like divide-and-conquer MCSS).

**D14.** A < B ⇔ 8n log n < 2n² ⇔ 4 log n < n. At n = 16: 4 · 4 = 16, equal, so not strictly faster. At n = 17: 4 · 4.09 ≈ 16.35 < 17 → **n0 = 17**.

**D15.** 100n < n² ⇔ n > 100. So **A is faster when n > 100**. For n = 50 pick **B** (2,500 vs 5,000 operations). For n = 5,000 pick **A** (500,000 vs 25,000,000).

**D16.** The test runs at i = 0 (2), i = 1 (9) and i = 2 (5, stops) → **3 tests**. Best-case input: 5 first, e.g. **5 1 2 3 4** → 1 test, O(1). Worst-case input: 5 absent, e.g. **1 2 3 4 6** → n tests plus the exit check, O(n).

**D17.** 34: mid = 3 (22), 34 > 22 → low = 4; mid = 5 (34) → **found, keys 22, 34**. 20: mid = 3 (22), 20 < 22 → high = 2; mid = 1 (12) → low = 2; mid = 2 (19) → low = 3 > high → **null, keys 22, 12, 19**.

**D18.** (a) 10, 15, 20, 25, 30. (b) 4, 6, 6, 5, 6 (sums 4, 12, 18, 20, 30 divided by 1 … 5).

**D19.**
- (a) curS: 5 → −4, which resets to 0 → 6 → 4 → 7. **maxS = 7** (6, −2, 3).
- (b) curS: −2 resets to 0 → 11 → 7 → 20 → 15 → 13. **maxS = 20** (11, −4, 13).

**D20.** Left half 4, −3, 5, −2: MCSS = **6** (4 − 3 + 5). Right half −1, 2, 6, −2: MCSS = **8** (2 + 6).
Max left-border sum, going left from −2: −2, 3, 0, 4 → **4**. Max right-border sum, going right from −1: −1, 1, 7, 5 → **7**.
Spanning = 4 + 7 = 11. Answer = max(6, 8, 11) = **11** (4, −3, 5, −2, −1, 2, 6).

**D21.** 1, −3, 4, −1, 2, 1, −5, 4 → **6** (4, −1, 2, 1). 2, −1, 2, −1, 2 → **4** (the whole sequence).

**D22.** **Linear search**: best case O(1) (key at the first position), worst case O(n) (key missing or last). The gap grows with n, so it is more than a constant.
