# Chapter 4: Sorting, "Justify Your Choice" Questions

Fifty open-ended scenario questions in the style of the instructor's sample:

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

## Question 5. Smartwatch heart rate

A smartwatch keeps the **last 20 heart-rate readings** and sorts them **once a minute** to show the median on the screen. The watch has **very little memory** and the code must be as **simple** as possible.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 6. Tournament scoreboard

An online chess tournament has **10,000 players** ranked by points. After each round only **about 20 players** change score, and each of them moves only **a few places** up or down. The ranking must be re-sorted after every round.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 7. Small pieces inside quicksort

A library's quicksort is fast on large arrays, but profiling shows that most of its time goes on **recursive calls on tiny subarrays of fewer than 16 elements**. The developers want to hand those tiny subarrays to a different algorithm.

**Which sorting algorithm would you choose for the small subarrays? Please justify your answer.**

---

## Question 8. Card game hand

In a card game app, a player is dealt **13 cards one at a time**, and the hand on screen must be **sorted after every card** arrives.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 9. Stable and in-place

A school system must sort **500 student records** by grade. Students with the **same grade must stay in their current (alphabetical) order**, and the system **cannot allocate a second array**.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 10. Flash memory wear

A data logger stores **1,000 readings on flash memory**. Reading is cheap, but **every write wears out the memory**, so the sort must **write to memory as few times as possible**. Running time matters much less.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 11. Contacts by city

A phone holds **2,000 contacts already sorted alphabetically by name**. The user taps "group by city". Contacts must be sorted by city, and **within each city they must still be in alphabetical order**.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 12. Spreadsheet sorting on two columns

An employee spreadsheet must be ordered **by department, and alphabetically by last name within each department**. The spreadsheet can only sort **one column at a time**.

**Which kind of sorting algorithm must the spreadsheet use, and in which order should the two columns be sorted? Please justify your answer.**

---

## Question 13. Java employee objects

A Java program holds an `ArrayList<Employee>` of **200,000 employees** in **order of hire date**. It must sort them by salary, and **employees with the same salary must stay in hire-date order**.

**Which sorting algorithm (and which Java method) would you choose? Please justify your answer.**

---

## Question 14. Exam marks with student records

A course has **1,200 students**. Each record holds a student number, a name and an **integer mark from 0 to 100**. The list is in **student-number order**. You must print the records ranked by mark, and **students with equal marks must stay in student-number order**.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 15. Log file larger than memory

A laptop with **2 GB of RAM** must sort a **10 GB log file** by timestamp. The log is **not sorted at all**.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 16. Linked list of customers

A program keeps **5 million customer records in a singly linked list** in memory and must sort them by customer ID.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 17. Two companies merge

Two companies merge. Company A has **3 million customers** and Company B has **2 million**, and each list is **already sorted by email address**. You must produce one combined list sorted by email.

**Which sorting algorithm (or part of one) would you use? Please justify your answer.**

---

## Question 18. Archival tape storage

A national archive keeps census records on **magnetic tape**. A tape can only be **read or written from start to end**; jumping to a random position takes minutes. The records must be sorted by household ID.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 19. Java array of integers

A Java program must sort an `int[]` of **1 million random integers** as fast as possible. Stability does not matter for primitive integers.

**Which sorting algorithm (and which Java method) would you choose? Please justify your answer.**

---

## Question 20. A server that suddenly got slow

A company's report server uses a quicksort that **always picks the last element as the pivot**. It has worked well for years. Then an upstream system changed and now sends the daily data **already sorted**. Sorting **1 million records** suddenly takes hours.

**Explain what happened, and which algorithm (or change) you would choose. Please justify your answer.**

---

## Question 21. Order statuses

An online store must sort **10 million orders by status**. There are only **5 possible statuses**: placed, paid, packed, shipped, delivered.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 22. Prices with cents

A price-comparison site must sort **2 million product prices**. Every price is in dollars and cents (for example `$19.99`) and **no price is above $5,000.00**.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 23. Flight control computer

An aircraft's flight control computer sorts **radar contacts by distance** every cycle. The sort **must finish within a fixed time limit every single time**, and the software is **not allowed to allocate extra memory** while flying.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 24. Medical device without recursion

A pacemaker's firmware must sort a **log of 5,000 events**. Its coding standard **forbids recursion** (the stack is tiny), **forbids extra arrays**, and requires a **guaranteed worst-case running time**.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 25. Public sorting web service

A public web API lets **anyone upload an array of up to 1 million numbers** and returns it sorted. The team worries that **attackers will craft inputs** designed to make the server as slow as possible.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 26. "Bubble sort is simpler"

A colleague proposes **bubble sort** for sorting **1 million customer records** every night, because "it's simple and easy to get right".

**Which sorting algorithm would you choose instead? Please justify your answer.**

---

## Question 27. Shellsort in production

A blog post suggests using **shellsort with Hibbard's gap sequence** to sort **1 million records** in a production system.

**Would you follow this advice? Which algorithm would you choose? Please justify your answer.**

---

## Question 28. Top 100 songs from a stream

A music service receives a **stream of 80 million (song, play count) records** every day. It must report the **100 most-played songs**, but the server **cannot store all 80 million records** in memory at once.

**Which algorithm or data structure would you choose? Please justify your answer.**

---

## Question 29. Median house price

A real-estate board has **2 million house sales** for the year in an unsorted array and needs the **median sale price**, just once.

**Would you sort the data? Which algorithm would you choose? Please justify your answer.**

---

## Question 30. Cheapest and most expensive flight

A travel site has **10,000 fares** for a route and must show **both the cheapest and the most expensive** one, using **as few comparisons as possible**.

**Which algorithm would you choose, and how many comparisons does it need? Please justify your answer.**

---

## Question 31. Gold and silver medals

**64 runners** have finished a race. You must find the **fastest and second-fastest** times with **as few comparisons as possible**.

**Which algorithm would you choose, and how many comparisons does it need? Please justify your answer.**

---

## Question 32. First page of search results

An online store's search returns **200,000 matching products**. The page shows only the **50 cheapest, in order of price**, and almost nobody clicks to page 2.

**Which algorithm would you choose? Please justify your answer.**

---

## Question 33. 90th percentile response time

An operations team has **50 million web-request response times** in an unsorted array and needs the **90th percentile** (the value 90% of requests are faster than), computed once per day.

**Which algorithm would you choose? Please justify your answer.**

---

## Question 34. Lowest reading

A sensor network has **1 million readings** in an unsorted array, and you only need the **single lowest reading**.

**Which algorithm would you choose, and how many comparisons does it need? Please justify your answer.**

---

## Question 35. Emergency room triage

An emergency room receives patients **continuously**. Each has a severity score, and the **most severe patient must always be treated next**. Nobody ever needs the full sorted list.

**Which algorithm or data structure would you choose? Please justify your answer.**

---

## Question 36. Running median of a sensor stream

Temperature readings arrive **one at a time, forever**. After every new reading, a dashboard must show the **median of all readings so far**.

**Which data structure(s) would you choose? Please justify your answer.**

---

## Question 37. Ages of every Canadian

Statistics Canada must sort **40 million people by age**. Ages are **whole numbers from 0 to 120**, and only the ages need to be in order.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 38. Ontario Education Numbers

The Ministry of Education must sort **2 million students** by their **9-digit Ontario Education Number**.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 39. Birth dates

A registry must sort **3 million birth records** by date of birth. Each date is stored as three integers: **year (1900–2026), month (1–12) and day (1–31)**.

**Which sorting algorithm would you choose, and in what order would you process the fields? Please justify your answer.**

---

## Question 40. Integers up to n²

You must sort **n = 1 million integers**, each in the range **[0, n² − 1]** (up to 10¹²).

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 41. Invoice numbers stored as text

An accounting system stores **800,000 invoice numbers as strings** ("7", "20", "100", …), each at most 7 digits. Sorting them as strings puts "100" before "20", which confuses the accountants.

**What would you do, and which sorting algorithm would you choose? Please justify your answer.**

---

## Question 42. IP addresses in a firewall log

A firewall log has **50 million entries** to be sorted by **IPv4 address**. An address has **4 parts, each an integer from 0 to 255** (for example `192.168.4.17`).

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 43. Lottery tickets

A lottery office must sort the **30 winning ticket numbers** of the week. Each ticket number has **9 digits**.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 44. Letter grades

A college must rank **5,000 student records by letter grade**. There are **13 possible grades** (A+, A, A−, B+, … F). Students with the same grade must **stay in their current order**.

**Which sorting algorithm would you choose? Please justify your answer.**

---

## Question 45. Duplicate email addresses

A mailing list has **5 million email addresses**. You must find out **whether any address appears more than once**.

**How would you use sorting to solve this, and which sorting algorithm would you choose? Please justify your answer.**

---

## Question 46. Customers on both lists

Two mailing lists have **1 million email addresses each**, and neither is sorted. You must find **every address that appears on both lists**.

**How would you use sorting to solve this, and which sorting algorithm would you choose? Please justify your answer.**

---

## Question 47. Most frequent words in a book

You have a **5-million-word book** and must report the **20 most frequent words**.

**Which sorting algorithm(s) would you use, and how? Please justify your answer.**

---

## Question 48. Decreasing order with heapsort

You must sort **100,000 scores in decreasing order** (highest first) using **in-place heapsort**.

**Which kind of heap would you use, and why? Please justify your answer.**

---

## Question 49. 3D points

A 3D modelling program must sort **1 million points (x, y, z)** in lexicographic order: by x, then by y for equal x, then by z for equal x and y. The coordinates are real numbers.

**Which sorting algorithm would you choose, and how? Please justify your answer.**

---

## Question 50. Sorted file with new records at the end

A file of **2 million records is sorted by ID**, except that **300 new records were appended at the end in random order**.

**Which algorithm (or combination) would you choose to make the whole file sorted? Please justify your answer.**

---
---

# Answer key

Quick check: the algorithm for each question. Read the full answers below for the justification.

| Q | Answer | Q | Answer | Q | Answer |
|---|---|---|---|---|---|
| 1 | insertion sort | 18 | mergesort | 35 | heap (priority queue) |
| 2 | external mergesort (k-way merge) | 19 | dual-pivot quicksort (`Arrays.sort`) | 36 | two heaps |
| 3 | radix sort | 20 | random-pivot quicksort | 37 | counting sort |
| 4 | random-pivot quicksort | 21 | bucket sort | 38 | radix sort |
| 5 | insertion sort | 22 | cents → bucket/counting sort | 39 | radix sort: day, month, year |
| 6 | insertion sort | 23 | heapsort | 40 | radix sort, base n |
| 7 | insertion sort | 24 | heapsort | 41 | convert to integers → radix sort |
| 8 | insertion sort | 25 | random-pivot quicksort / heapsort | 42 | radix sort, base 256 |
| 9 | insertion sort | 26 | quicksort (not bubble) | 43 | insertion sort |
| 10 | selection sort | 27 | quicksort/heapsort (not shellsort) | 44 | bucket sort |
| 11 | mergesort | 28 | min-heap of size 100 | 45 | sort + scan neighbours |
| 12 | stable sort, name first | 29 | quickselect | 46 | sort both + merge-scan |
| 13 | mergesort (`Collections.sort`) | 30 | pairs: 3n/2 − 2 | 47 | sort + count + heap |
| 14 | bucket sort | 31 | tournament: n + ⌈log n⌉ − 2 | 48 | min-heap |
| 15 | external mergesort | 32 | quickselect + sort 50 / heap | 49 | comparator + mergesort |
| 16 | mergesort | 33 | quickselect | 50 | sort new 300 + merge |
| 17 | merge step only | 34 | linear scan: n − 1 | | |

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

## Question 5. Insertion sort

- n = 20 is tiny, so even the O(n²) worst case is at most about 190 comparisons.
- It is **in-place** (O(1) extra memory) and a few lines of code. The slides recommend the simple sorts for **small data (< 1K)**.
- Readings change only a little from minute to minute, so the array is often nearly sorted, which is insertion sort's **O(n) best case**.
- **Why not the others:** mergesort needs an extra array; quicksort and heapsort add code and overhead for no benefit at n = 20.

## Question 6. Insertion sort

- After a round the ranking is **nearly sorted**: only about 20 players are out of place, each by a few positions.
- Insertion sort only moves an element past the elements it is out of order with. Here that is about 20 players × a few places, so the work is close to **O(n)**, its best case on sorted input.
- It is in-place and **stable**, so tied players keep their previous order.
- **Why not the others:** mergesort and heapsort always do O(n log n) ≈ 130,000 comparisons and ignore the existing order; quicksort with an end pivot is at its **O(n²) worst case** on sorted input.

## Question 7. Insertion sort

- On tiny arrays the constant factors matter more than the growth rate. Insertion sort has almost **no overhead**: no recursion, no pivot choice, no partitioning.
- Subarrays near the bottom of quicksort's recursion are small, so insertion sort's O(n²) is only about 16²/2 = 128 steps at most.
- It is in-place, so it fits inside an in-place quicksort.
- This is how real hybrid sorts work, as the [study guide](../study-guide.md) notes: insertion sort for small pieces, quicksort or mergesort for the big picture.

## Question 8. Insertion sort

- The hand is **always sorted** before the next card arrives, so each new card needs **one insertion step**: slide it left past larger cards. That is O(n) per card, with n ≤ 13.
- This is exactly how people sort cards by hand.
- **Why not the others:** re-sorting the whole hand with mergesort, quicksort or heapsort after every card ignores the existing order.

## Question 9. Insertion sort

- The constraints are **stable + in-place**. Insertion sort is the only algorithm from the slides with both properties that is reasonable here.
- n = 500, so O(n²) ≈ 125,000 steps at worst, which is fast.
- **Why not the others:**
  - **Mergesort:** stable but needs an O(n) extra array.
  - **Quicksort, heapsort, selection sort:** in-place but **not stable**.
  - **Bubble sort:** stable and in-place too, but slower than insertion sort in practice.

## Question 10. Selection sort

- Selection sort finds the minimum of the unsorted part and does **one swap per pass**, so at most **n − 1 swaps** (about 2n writes) in total, whatever the input.
- **Insertion and bubble sort** can do **O(n²) writes**, because they shift or swap elements many times.
- It is in-place, so there are no extra writes into a second array.
- Its O(n²) comparisons only read memory, which the question says is cheap, and n = 1,000 is small.
- **Why not the others:** mergesort writes every element on every level (O(n log n) writes); quicksort and heapsort also swap far more than n − 1 times.

## Question 11. Mergesort (stable)

- The requirement "within each city still alphabetical" means the sort must be **stable**: contacts with equal cities keep their current (alphabetical) order.
- Mergesort is **stable** and O(n log n) ≈ 2,000 × 11 = 22,000 comparisons.
- **Why not the others:** quicksort, heapsort and selection sort are **not stable** and could shuffle names within a city. Insertion sort is stable but O(n²) ≈ 2 million steps on random city order.

## Question 12. A stable sort, least significant column first

- Sort by **last name first**, then sort by **department** with a **stable** sort.
- The second sort puts departments in order, and stability keeps employees with the same department in the alphabetical order created by the first sort.
- This is the idea behind **lexicographic and radix sort**: process the **least significant key first** and use a stable sort on each pass.
- If the sort were not stable (quicksort, heapsort), the second pass would scramble the names within each department.
- Sorting by department first and then by name would end with the list ordered by name only, which is wrong.

## Question 13. Mergesort, via `Collections.sort`

- Equal salaries must keep **hire-date order**, so the sort must be **stable**.
- `Collections.sort` (Java 8) uses **mergesort**, and the specification requires it to be **stable** even if the implementation changes.
- Use a `Comparator` on salary: `list.sort(Comparator.comparing(Employee::getSalary))` or `Collections.sort(list, ...)`.
- O(n log n) ≈ 200,000 × 18 = 3.6 million comparisons.
- **Why not the others:** a hand-written quicksort or heapsort is not stable. (`Arrays.sort` on primitives uses dual-pivot quicksort, which is not stable, but that does not matter for primitives. Objects are a different case.)

## Question 14. Bucket sort

- Keys are integers in **[0, 100]**, so N = 101 buckets.
  - Phase 1: put each record into bucket B[mark], O(n).
  - Phase 2: read buckets 0 … 100 in order, O(n + N).
  - Total **O(n + N)** = O(1,200 + 101), i.e. linear.
- Bucket sort is **stable**: records enter each bucket in student-number order and come out in the same order. That is the tie rule the question asks for.
- Bucket sort **moves whole records** (key, element).
- **Why not counting sort:** the slides' counting sort only counts how many times each value appears and then rewrites the values 0, 0, 1, 1, 1 … into the array. The names and student numbers are lost, so it only works when the keys themselves are the data.
- **Why not comparison sorts:** O(n log n), and quicksort and heapsort are not stable.

## Question 15. External mergesort

1. **Create runs:** read 2 GB at a time, sort it in memory (quicksort or heapsort), and write it back as a sorted run. This gives **5 sorted runs**.
2. **Merge:** merge the 5 runs with a multi-way merge, reading each run sequentially and writing the output sequentially.

- Mergesort accesses data **sequentially**, which suits disk, and only needs a small buffer per run. The slides recommend mergesort for **huge data and external sorting**.
- **Why not the others:** in-place quicksort and heapsort need the **whole 10 GB in memory** and jump randomly through the array; on disk, random access is extremely slow.

## Question 16. Mergesort

- Mergesort only needs **sequential access**: split the list by walking it, and merge by repeatedly taking the smaller front node.
- On a linked list, merging **relinks nodes** instead of copying them into a second array, so it needs no O(n) buffer. It stays O(n log n) and **stable**.
- **Why not the others:**
  - **In-place quicksort** walks inward from both ends, but a singly linked list cannot step backwards.
  - **Heapsort** needs O(1) access by index (children at 2i and 2i + 1), which a linked list cannot provide.
  - A random pivot would also require walking the list to reach it.

## Question 17. The merge step of mergesort

- Both lists are **already sorted**, so no sorting is needed, only the **merge**: compare the fronts and move the smaller to the output until one list is empty, then copy the rest.
- **O(n + m)** = about 5 million steps, with sequential access, so it also works if the lists are on disk.
- It is stable (on a tie, take from list A first).
- **Why not re-sort:** concatenating and running any O(n log n) sort (≈ 5M × 22 ≈ 110M comparisons) throws away the order you already have.

## Question 18. Mergesort

- Mergesort is the classic tape sort. Both **splitting and merging read and write strictly from start to end**, and each merge pass streams through the tapes once.
- O(n log n) total, with only O(log n) passes over the data.
- **Why not the others:** quicksort's partitioning and heapsort's upheap/downheap jump to **random positions**, which takes minutes each time on tape.

## Question 19. Quicksort (dual-pivot), via `Arrays.sort`

- `Arrays.sort(int[])` uses **dual-pivot quicksort**, which the slides say is faster than single-pivot quicksort.
- Quicksort is **in-place** and has the best constants in practice: O(n log n) average ≈ 1M × 20 = 20 million comparisons.
- Stability is meaningless for primitive ints, because equal ints are indistinguishable.
- **Why not the others:** mergesort needs O(n) extra memory; heapsort is O(n log n) but slower in practice. Counting sort is impossible because random ints span about 4 billion values.

## Question 20. Randomized quicksort (random pivot)

- **What happened:** on sorted input, the last element is always the **maximum**, so each partition gives L = n − 1 and G = 0. The recursion depth becomes n and the total work is **n(n − 1)/2 ≈ 5 × 10¹¹** comparisons for n = 1 million. That is **O(n²)**, the slides' worst case.
- **Fix:** choose the pivot **at random** (or use median of three). Each call is then "good" with probability ½, the expected height is O(log n), and the expected time is **O(n log n)** ≈ 2 × 10⁷, whatever the input order.
- Heapsort or mergesort would also be acceptable, since both are O(n log n) in every case.

## Question 21. Bucket sort

- There are only **N = 5 distinct keys**: map placed = 0, paid = 1, packed = 2, shipped = 3, delivered = 4.
- Bucket sort: one pass to drop each order into its bucket, then concatenate the 5 buckets. **O(n + N) = O(n)**, about 10 million steps, and it is **stable**.
- **Why not the others:** any comparison sort needs O(n log n) ≈ 10M × 23 ≈ 230 million comparisons. Quicksort in particular wastes effort on so many equal keys unless it splits off the "equal" group E.

## Question 22. Convert to cents, then bucket (or counting) sort

- Multiply each price by 100: every price becomes an **integer number of cents in [0, 500,000]**, so N = 500,001.
- Bucket sort is then **O(n + N)** = O(2,000,000 + 500,001) ≈ 2.5 million steps, versus O(n log n) ≈ 2M × 21 ≈ 42 million comparisons. Use counting sort if only the prices themselves are needed.
- This works **because prices have exactly two decimals**. Arbitrary real numbers (like the temperatures in Question 4) cannot be mapped to a small integer range, so a comparison sort is used there.

## Question 23. Heapsort

- Heapsort is **O(n log n) in the worst case**, so the time limit can be guaranteed for every cycle.
- It is **in-place**, needing O(1) extra memory, so nothing is allocated during flight.
- **Why not the others:**
  - **Quicksort** has an O(n²) worst case; even with a random pivot it is only fast *on average*, which is not a guarantee.
  - **Mergesort** guarantees O(n log n) but needs an **O(n) extra array**.
  - **Index-based sorts** need extra arrays of buckets or counters.

## Question 24. Heapsort

- Heapsort can be written **without recursion**: upheap and downheap are simple loops that move up or down the tree by index.
- It is **in-place** (no extra arrays) and **O(n log n) in the worst case**, which meets all three rules.
- **Why not the others:**
  - **Quicksort** is naturally recursive, using O(log n) stack on average and **O(n) in the worst case**, and its worst case is O(n²).
  - **Mergesort** needs an extra array.
  - **Insertion and selection sort** satisfy the rules, but they are O(n²) ≈ 12.5 million steps for n = 5,000, versus about 60,000 for heapsort.

## Question 25. Randomized quicksort (or heapsort for a hard guarantee)

- With a **fixed pivot rule** (first, last or middle element), an attacker can build an input where every pivot is the min or max, forcing **O(n²)** ≈ 5 × 10¹¹ steps. That makes a denial-of-service attack.
- With a **random pivot**, the attacker cannot predict the pivots, so the expected time is **O(n log n) for every input**.
- If the service must *guarantee* a time limit, use **heapsort** (O(n log n) worst case, in-place) or mergesort (O(n log n) worst case, O(n) extra memory). No input can slow them down.

## Question 26. Quicksort (or mergesort/heapsort), not bubble sort

- Bubble sort is **O(n²)**: for n = 1 million that is about 10¹² comparisons, which takes hours to days.
- An O(n log n) sort needs about 1M × 20 = **2 × 10⁷** comparisons, roughly **50,000 times fewer**.
- The slides limit the simple O(n²) sorts to **small data (< 1K)**. For large data (1K–1M) they recommend **quicksort or heapsort**, and **mergesort for huge data (> 1M)**.
- "Simple" is not an advantage when every language already ships a tested O(n log n) sort (`Arrays.sort`, `Collections.sort`).

## Question 27. No: use quicksort (or heapsort/mergesort)

- Shellsort with Hibbard's gaps has a worst case of **O(n^(3/2))**: for n = 1 million that is about 10⁹ steps, versus about 2 × 10⁷ for an O(n log n) sort.
- The slides describe shellsort as being of **academic interest only**.
- For 1 million records, use **quicksort** (fastest on average, in-place), **heapsort** (guaranteed O(n log n), in-place) or **mergesort** (stable, sequential access).

## Question 28. A min-heap of size 100 (no full sort)

- Keep a **min-heap of the best 100 songs seen so far**, keyed on play count. For each new record:
  - if the heap has fewer than 100 items, insert it;
  - otherwise, if the record beats the heap's **minimum**, removeMin and insert the new record.
- Each record costs **O(log k)** with k = 100, so the total is **O(n log k)** ≈ 80M × 7. Memory is only **O(k)** = 100 records.
- At the end, removeMin 100 times to get the top 100 in order.
- **Why not the others:**
  - Sorting all 80 million records needs them all in memory (or an external mergesort) and O(n log n) work for 100 answers.
  - The leaderboard approach (build a max-heap in O(n), then extract 10) also needs all records in memory at once.

## Question 29. Quickselect (no sorting)

- The median is the k-th smallest value with **k = n/2**. **Quickselect** (prune-and-search) finds it in **O(n) on average**: partition around a random pivot, then recurse **only into the side that contains position k**.
- That is roughly a few million steps, versus O(n log n) ≈ 2M × 21 ≈ 42 million comparisons to sort everything.
- Sorting is wasteful here: it puts all 2 million prices in order to read just one.
- (Heap-based selection would cost O(n + k log n) with k = 1 million, which is no better than sorting.)

## Question 30. Compare in pairs: 3n/2 − 2 comparisons

- Pair up the fares and compare each pair (n/2 comparisons). The smaller of each pair is a min candidate and the larger is a max candidate.
- Find the min of the n/2 smaller ones (n/2 − 1 comparisons) and the max of the n/2 larger ones (n/2 − 1 comparisons).
- Total **3n/2 − 2** = 3 × 10,000/2 − 2 = **14,998 comparisons**, which is the slides' **lower bound** for finding both min and max.
- **Why not the others:** two separate scans need 2(n − 1) = 19,998 comparisons; sorting needs about 130,000.

## Question 31. Tournament: n + ⌈log n⌉ − 2 comparisons

- Run a **knockout tournament**: 63 comparisons (n − 1) find the winner.
- The second-fastest runner must have **lost directly to the winner**. The winner played ⌈log₂ 64⌉ = 6 matches, so compare those 6 runners: 5 more comparisons.
- Total **n + ⌈log n⌉ − 2** = 64 + 6 − 2 = **68 comparisons**, the slides' lower bound for the two smallest (here, the two fastest).
- **Why not the others:** finding the minimum and then scanning again for the second needs 63 + 62 = 125 comparisons; a full sort needs even more.

## Question 32. Quickselect then sort the 50 (or a heap)

- **Option A:** use **quickselect** to find the 50th-cheapest price, partition around it (O(n) on average), then sort only those 50 items (O(k log k)). Total **O(n + k log k)**.
- **Option B:** **build a min-heap** of all 200,000 in **O(n)** (bottom-up), then removeMin **50 times**, O(k log n). Total **O(n + k log n)**.
- Either costs roughly 200,000 + 1,000 steps, versus O(n log n) ≈ 200,000 × 18 = 3.6 million to sort everything for a page nobody scrolls past.
- If the user does go to page 2, just run the selection again for k = 100.

## Question 33. Quickselect

- The 90th percentile is the k-th smallest value with **k = 0.9n** = 45 million. **Quickselect** finds it in **O(n) average** time: partition around a random pivot, then recurse into one side only.
- That is roughly a few times 50 million steps, versus O(n log n) ≈ 50M × 26 ≈ 1.3 billion comparisons to sort.
- Quickselect can be done **in-place**, so it needs no second 50-million-entry array.
- Heap-based selection would cost O(n + k log n) with k = 45 million, which is worse than sorting.

## Question 34. A single linear scan: n − 1 comparisons

- Keep the smallest value seen so far and compare it with every other reading: **n − 1 = 999,999 comparisons**, O(n), O(1) extra memory.
- The slides show that **n − 1 is also the lower bound**: every reading except the winner must "lose" at least one comparison, so no algorithm can do better.
- **Why not sort:** sorting costs O(n log n) ≈ 20 million comparisons to answer a question that needs one pass.

## Question 35. A heap (priority queue)

- A heap keyed on severity supports **insert in O(log n)** (upheap) and **removeMax in O(log n)** (downheap). The most severe patient is always at the **root**, readable in O(1).
- Patients keep arriving, so sorting would have to be repeated after every arrival, costing **O(n log n) each time**.
- This is the slides' **priority queue** application (OS scheduling works the same way).
- **Why not a sorted list:** insert into a sorted list is O(n) per patient; an unsorted list makes finding the most severe O(n) each time.

## Question 36. Two heaps

- Keep a **max-heap of the smaller half** of the readings and a **min-heap of the larger half**, with sizes differing by at most 1.
- **New reading:** insert it into the correct heap (O(log n)). If the sizes become unbalanced by 2, move one root to the other heap (O(log n)).
- **Median:** the root of the larger heap, or the average of both roots when the sizes are equal, read in **O(1)**.
- **Why not the others:** re-sorting after every reading costs O(n log n) each time; quickselect each time costs O(n) each time.

## Question 37. Counting sort

- Ages are integers in **[0, 120]**, so N = 121 counters. Count each age (one pass), then rewrite the array from the counters: **O(n + N) = O(n)** ≈ 40 million steps.
- Only the **ages themselves** need to be sorted, with no records attached, so counting sort's "rewrite the values from the counts" approach is fine. (With names attached, use bucket sort, as in Question 14.)
- **Why not comparison sorts:** O(n log n) ≈ 40M × 25 = about 1 billion comparisons, 25 times more.

## Question 38. Radix sort

- Each OEN is a **9-digit** number: d = 9 digits, each in [0, 9] (N = 10).
- Radix sort does 9 stable bucket-sort passes, **least significant digit first**: **O(d(n + N))** = 9 × (2M + 10) ≈ **18 million** bucket placements.
- **Why not the others:**
  - **Comparison sorts:** O(n log n) ≈ 2M × 21 ≈ 42 million comparisons.
  - **Counting sort on the whole number:** needs N = 10⁹ counters, far more than n, so O(n + N) is dominated by N.

## Question 39. Radix (lexicographic) sort: day, then month, then year

- Each date is a 3-tuple. Use a **stable bucket sort on each field**, starting with the **least significant**:
  1. **day** (N = 31)
  2. **month** (N = 12)
  3. **year** (shift 1900–2026 to 0–126, N = 127)
- Stability keeps the day order within each month, and the month order within each year.
- **Running time:** O(3n + 31 + 12 + 127) = **O(n)** ≈ 9 million steps, versus O(n log n) ≈ 3M × 22 ≈ 66 million comparisons.
- Sorting by year first would be wrong: the later passes would destroy the year order.

## Question 40. Radix sort with base n

- **Counting sort** would need N = n² = 10¹² counters, so it runs in O(n + N) = **O(n²)**, which is hopeless.
- Instead, write each key in **base n**: every key in [0, n² − 1] has exactly **d = 2 digits**, each in [0, n − 1].
- **Radix sort:** 2 bucket-sort passes with N = n buckets each, giving **O(d(n + N)) = O(2(n + n)) = O(n)**.
- That is about 4 million steps, versus O(n log n) ≈ 20 million comparisons.

## Question 41. Convert to integers, then radix sort

- **The bug:** strings compare **character by character**, so "100" < "20" because '1' < '2'. The slides warn about exactly this ("14" < "2").
- **Fix:** convert each string to an **integer** (or pad every string with leading zeros to 7 digits: "0000020" < "0000100").
- **Sort:** 7-digit numbers mean d = 7 and N = 10, so radix sort runs in O(7(n + 10)) = **O(n)** ≈ 5.6 million steps, versus O(n log n) ≈ 800k × 20 ≈ 16 million comparisons.
- A comparison sort on the converted integers would also be correct; the conversion is the key point.

## Question 42. Radix sort (base 256)

- An IPv4 address is a **4-tuple of integers in [0, 255]**: d = 4, N = 256.
- Radix sort: 4 stable bucket-sort passes, **last part first** (`17`, then `4`, then `168`, then `192`).
- **Running time:** O(d(n + N)) = 4 × (50M + 256) ≈ **200 million** placements, versus O(n log n) ≈ 50M × 26 ≈ 1.3 billion comparisons.
- **Why not counting sort on the whole 32-bit address:** it would need N = 2³² ≈ 4.3 billion counters.

## Question 43. Insertion sort (any simple sort)

- n = 30 is **tiny**: insertion sort needs at most about 30²/2 = 435 comparisons.
- **Why not the others:**
  - **Counting sort:** N = 10⁹ counters for 30 numbers.
  - **Radix sort:** 9 passes × (30 + 10 buckets) ≈ 360 bucket operations, more setup and code for no gain.
- Index-based sorts only pay off when **n is large compared with the key range** (or the number of digits). For tiny n, a simple comparison sort wins.

## Question 44. Bucket sort

- Map the 13 grades to integers: A+ = 0, A = 1, A− = 2, … F = 12, so N = 13.
- Bucket sort: drop each record into B[grade], then concatenate the buckets. **O(n + N) = O(n)**, about 5,000 steps, and it is **stable**, so students with the same grade keep their current order as required.
- Bucket sort carries the **whole record** (key, element).
- **Why not the others:** counting sort would lose the records (it only rewrites values); comparison sorts are O(n log n) and quicksort/heapsort are not stable.

## Question 45. Sort, then compare neighbours

- After sorting, **any duplicates sit next to each other**. One pass comparing each address with the next finds them: n − 1 comparisons.
- Total **O(n log n)** for the sort plus O(n) for the scan, about 5M × 22 ≈ 110 million comparisons. Use **quicksort** (in-place, fastest on average) or **mergesort** if the data is on disk.
- **Why not the others:** comparing every pair of addresses is O(n²) ≈ 1.25 × 10¹³ comparisons.
- (From Chapter 2: a **hash table** finds duplicates in **O(n) expected** time. Sorting is the comparison-based alternative and needs no hash function.)

## Question 46. Sort both lists, then merge-scan

1. **Sort** each list: O(n log n) each, with quicksort or mergesort.
2. **Scan both sorted lists together**, like mergesort's merge: compare the two fronts; if they are equal, output the address and advance both; otherwise advance the smaller one.

- The scan is **O(n + m)**. Total ≈ 2 × (1M × 20) + 2M ≈ **42 million** steps.
- **Why not the others:** checking each address of list A against every address of list B is O(n · m) = **10¹² comparisons**.
- A hash table (Chapter 2) would also work, in O(n + m) expected time.

## Question 47. Sort the words, count runs, then use a heap for the top 20

1. **Sort** all 5 million words (quicksort or mergesort, comparing strings), O(n log n). Equal words become **adjacent**.
2. **Count runs** of equal words in one pass, O(n). This gives d (word, count) pairs, where d is the number of distinct words (perhaps 50,000).
3. **Top 20:** build a max-heap on count in O(d) and removeMax 20 times, O(20 log d). Quickselect would also work.

- **Why not the others:** sorting the d pairs by count in step 3 costs O(d log d) for only 20 answers, which is wasteful but acceptable.
- Using a hash table (Chapter 2) for counting would replace step 1 with O(n) expected time.

## Question 48. A min-heap

- In-place heapsort repeatedly **removes the root** and stores it at the **end of the array**, just past the shrinking heap.
- With a **min-heap**, the smallest remaining score goes to the end each time, so the array ends up **largest first**: decreasing order. The slides' example on 6, 2, 7, 9, 5 gives **9 7 6 5 2**.
- For **increasing** order you would use a **max-heap** (the slides' "reverse comparator").
- Heapsort is O(n log n) in every case and in-place, about 100,000 × 17 ≈ 1.7 million comparisons.

## Question 49. A comparison sort with a lexicographic comparator (e.g. mergesort)

- Write a **comparator** that compares x first, then y if the x values are equal, then z if the y values are also equal. Sort once with an O(n log n) comparison sort: **mergesort** (stable, `Collections.sort`) or **quicksort**. About 1M × 20 = 20 million comparisons.
- **Alternative:** lexicographic sort by passes, **z first, then y, then x**, each with a **stable** sort.
- **Why not radix or bucket sort:** the coordinates are **real numbers**, not integers in a small range [0, N − 1], so they cannot be used as bucket indexes. If they were small integers, radix sort over the 3 coordinates would be O(n).

## Question 50. Sort the 300 new records, then merge

1. **Sort the 300 new records** on their own, with insertion sort or quicksort. O(k log k) with k = 300, which is trivial.
2. **Merge** the 2 million sorted records with the 300 sorted ones (mergesort's merge step): **O(n + k)** ≈ 2 million steps, with sequential access.

- **Why not the others:**
  - Re-sorting all 2,000,300 records with an O(n log n) sort (≈ 42 million comparisons) ignores the existing order.
  - **Insertion sort on the whole file:** each new record may move up to 2 million places, about 300 × 2M = **600 million** moves.
  - **Quicksort with an end pivot** is near its O(n²) worst case on data this close to sorted.

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
| top k from a stream too big for memory | **min-heap of size k**, O(n log k) |
| only the min, or both min and max | **one scan** (n − 1) / **pairs** (3n/2 − 2), no sort |
| stable **and** in-place, small n | **insertion sort** |
| writes are expensive (flash memory) | **selection sort** (at most n − 1 swaps) |
| sort by key B within key A | **stable sort**, least significant key (B) first |
| sorted file plus a few new records | sort the new ones, then **merge**, O(n + k) |
| find duplicates / common items | **sort**, then scan neighbours or merge-scan |
