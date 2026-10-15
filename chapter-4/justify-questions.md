# Chapter 4: Sorting, "Justify Your Choice" Questions

Four open-ended scenario questions in the style of the instructor's sample:

> You are working on a computer science competition platform where the primary goal is to rank and sort a leaderboard of participants based on their scores and list the top ten. Each participant has a unique score, and there are millions of participants competing. Which sorting algorithm would you choose? Please justify your answer.

(Model answer for that one: **heap / heapsort**. Build a max-heap in O(n), then removeMax 10 times in O(k log n). See the [README](README.md#13-the-instructors-sample-questions).)

Write a full answer for each question before opening the answer key at the bottom. A strong answer has three parts:
1. **Name** the algorithm.
2. **Give its running time (and memory) in this scenario**, using the numbers in the question.
3. **Rule out the alternatives** by naming the constraint each one breaks.

Notes are in [README.md](README.md). The MCQ and hands-on question bank is in [questions.md](questions.md).

---

## Question 1. Airline check-in

An airline app keeps the passenger list for a flight **sorted by seat number** while check-in is open. The flight has **about 400 passengers**. Passengers check in **one at a time**, and after each check-in the new passenger must appear in the correct place in the list straight away. The list is shown on the gate agent's screen, so it must **always be fully sorted**.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 2. Bank transaction timeline

A bank's **50 branches** each produce a file of the day's transactions, **already sorted by timestamp**. Altogether there are **about 2 billion transactions** (hundreds of GB), far more than the server's RAM. The fraud team needs **one file of all transactions sorted by timestamp**. When two transactions have the **same timestamp, they must stay in the order the branch recorded them**.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 3. Canada Post delivery routes

Canada Post must sort **6 million parcels by postal code** every night to plan delivery routes. A Canadian postal code always has **6 characters** in the pattern letter–digit–letter digit–letter–digit (for example `N9B 3P4`). Speed matters most, and memory for extra arrays is available.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 4. Weather simulation data

A weather simulation produces **10 million temperature readings stored as `double` values** (for example `-12.73`, `21.405`) in one in-memory array. They must be sorted **as fast as possible on average**. The server has enough RAM for the array itself but **not for a second copy of it**. The readings are in **random order**, and **stability does not matter**.

**Which sorting algorithm would you choose? Please justify your answer.**

---
---

# Answer key

## Question 1. Insertion sort

- **Why it fits:** before each check-in the list is already sorted, so adding one passenger is a single **insertion step**: walk back from the end and slide larger seat numbers one place right until the new passenger's spot is found. That costs **O(n)** per check-in, at most about 400 moves. Insertion sort is **O(n) in the best case** (already sorted input), and here the list is sorted except for the one new item.
- It is **in-place**, simple, and the slides recommend it for **small data (< 1K)**.
- **Why not the others:**
  - Re-running **mergesort, heapsort or quicksort** after every check-in costs O(n log n) each time and ignores the fact that the list is already sorted.
  - **Quicksort** with the slides' last-element pivot is at its **worst case, O(n²)**, on sorted input, which is exactly what this list is.
  - **Counting/bucket sort** would rebuild everything from scratch each time.
- **Total over all check-ins:** n insertions × O(n) = O(n²) ≈ 160,000 steps for n = 400, which is trivial.

## Question 2. Mergesort (external, multi-way merge)

- **Why it fits:** the 50 files are already **sorted runs**, which is exactly what mergesort's **merge** step takes as input. The divide and recur steps are already done; only the conquer (merge) step remains.
  - Merge the files by repeatedly taking the earliest timestamp among the fronts of the 50 files.
  - Keep the 50 front items in a **min-heap** keyed on timestamp, so each step costs O(log 50).
  - Total **O(n log k)** with n = 2 billion and k = 50, which is close to linear.
- **Sequential access:** each file is read front to back and the output is written front to back, so it works on **disk** and only needs a small buffer per file in memory. The slides recommend mergesort for **huge data (> 1M)** and **external sorting** for this reason.
- **Stable:** on a tie, take from the file being read first. Records with equal timestamps then keep their recorded order, which the question requires.
- **Why not the others:**
  - **Quicksort and heapsort** jump around the array (random access), which is extremely slow on disk. They also need all 2 billion records in memory, and neither is stable.
  - **Counting/radix sort** over timestamps would need the whole dataset in memory and would not reuse the already sorted files.

## Question 3. Radix sort (lexicographic sort with a stable bucket sort per character)

- **Why it fits:** every key is a **fixed-length 6-tuple** of characters, and each character comes from a small alphabet:
  - letters map to integers 0–25 (N = 26)
  - digits map to 0–9 (N = 10)
- Do **6 passes of bucket sort**, from the **last character to the first** (least significant first), so `N9B 3P4` is sorted on `4`, then `P`, then `3`, and so on.
- Bucket sort is **stable**, so the order from earlier passes is kept within each bucket. That is what makes radix sort correct.
- **Running time:** O(d(n + N)) = O(6 × (6,000,000 + 26)) = **O(n)**, because d = 6 is constant and N ≤ 26 is tiny.
- **Why not the others:**
  - **Comparison sorts** (merge, quick, heap) take O(n log n): n log n ≈ 6M × 23 ≈ **138 million comparisons** versus about 36 million bucket placements. Each comparison is also a string comparison of up to 6 characters.
  - **Counting sort over the whole code as one number** needs N = 26 × 10 × 26 × 10 × 26 × 10 ≈ **17.6 million counters**, which is more than n. It is also impossible without first converting each code to an integer.

## Question 4. Quicksort with a random pivot

- **Why it fits:** quicksort is the slides' choice for **fast in-place sorting of in-memory arrays**. It runs in **O(n log n) average** with small constants, and in practice it is the fastest of the comparison sorts. With **n = 10 million**, n log n ≈ 10M × 23 ≈ 230 million comparisons.
- **In-place:** partitioning only swaps elements within the array, so it needs **no second copy**. The only extra space is the recursion stack, O(log n) expected.
- **Random pivot:** this makes the O(n²) worst case (pivot always the minimum or maximum) very unlikely on any input. Each call is "good" with probability ½, so the expected height is O(log n). Java's `Arrays.sort` for primitive `double[]` uses **dual-pivot quicksort** for this reason.
- Quicksort is not stable, but the question says stability does not matter.
- **Why not the others:**
  - **Mergesort:** needs an **O(n) extra array** for merging, which the server cannot afford.
  - **Heapsort:** also in-place and O(n log n) in every case, but slower on average in practice. A guaranteed worst case is not required here. If the question had demanded a guaranteed O(n log n) time limit, heapsort would be the answer instead.
  - **Counting, bucket and radix sort:** the keys are **real numbers**, not integers in a small range [0, N − 1], so they cannot be used as indexes.
  - **Insertion/selection sort:** O(n²) ≈ 10¹⁴ steps.

---

## Quick decision guide

| If the question says… | Think… |
|---|---|
| "top ten", "top k" out of millions | **heap**: build O(n), then k removals O(k log n) |
| already sorted / one new item / small list | **insertion sort** (O(n) on sorted input) |
| too big for memory, on disk, already sorted files, must be stable | **mergesort** (sequential access, stable) |
| guaranteed O(n log n), no extra memory | **heapsort** |
| fastest on average, in memory, no extra copy | **quicksort** with a random or dual pivot |
| integers in a small range (marks, ages) | **counting / bucket sort**, O(n + N) |
| fixed-length codes, IDs, dates, phone numbers | **radix sort**, O(d(n + N)) |
| median / k-th value only | **quickselect**, O(n) average |
