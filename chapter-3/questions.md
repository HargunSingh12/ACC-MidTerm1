# Chapter 3: Search Trees, Question Bank

Every question type from the Mid-Term I format, for **Chapter 3 only** (binary trees, BST, AVL, (2,4), red-black, splay). The answer key is at the bottom. Notes are in [README.md](README.md).

| Part | Exam section | Questions |
|---|---|---|
| A | MCQ Level I (simple) | A1–A18 |
| B | MCQ Level II (scenarios) | B1–B10 |
| C | Short answer Level I (fill in) | C1–C20 |
| D | Short answer Level II (hands-on) | D1–D24 |

**Tree notation:** `8[3[1,6],10[-,14]]` means root 8 with left child 3 (which has children 1 and 6) and right child 10 (which has only a right child, 14). `-` is an empty child. In red-black trees a B or R follows each key, e.g. `6B[3R,8R]`. BST and red-black deletions use the **inorder successor**, as the slides do.

---

## Part A. MCQ Level I

**A1.** The depth of a node is: (a) its number of children (b) its number of ancestors (c) the height of the tree (d) its number of descendants

**A2.** In a proper binary tree with i internal nodes, the number of external nodes is: (a) i (b) i − 1 (c) i + 1 (d) 2i

**A3.** Which traversal visits a node **between** its left and right subtrees? (a) preorder (b) inorder (c) postorder (d) Euler

**A4.** Which traversal is used to evaluate an arithmetic expression tree? (a) preorder (b) inorder (c) postorder (d) level order

**A5.** An inorder traversal of a BST outputs the keys: (a) in insertion order (b) in increasing order (c) in decreasing order (d) by level

**A6.** When deleting a BST node with two internal children, the slides copy in the key of: (a) the root (b) the inorder successor (c) the parent (d) any leaf

**A7.** Worst-case height of a BST with n keys: (a) O(1) (b) O(log n) (c) O(n) (d) O(n²)

**A8.** In an AVL tree, the heights of the two children of every node differ by at most: (a) 0 (b) 1 (c) 2 (d) log n

**A9.** After an AVL **insertion**, how many restructure operations at most are needed? (a) one (b) two (c) log n (d) n

**A10.** After an AVL **deletion**, rebalancing: (a) is never needed (b) needs exactly one restructure (c) may need restructures all the way up to the root (d) rebuilds the whole tree

**A11.** In a (2,4) tree, every internal node has: (a) exactly 2 children (b) at most 4 children (c) at least 4 children (d) 2 or 3 children

**A12.** Which is **not** a red-black tree property? (a) the root is black (b) red nodes have black children (c) all leaves have the same black depth (d) every node's subtree heights differ by at most 1

**A13.** A newly inserted (non-root) node in a red-black tree is coloured: (a) black (b) red (c) like its parent (d) double black

**A14.** For a red-black **insertion** with a double red and a **red uncle**, you: (a) restructure (b) recolour (c) delete the node (d) do nothing

**A15.** Red-black **deletion** Case 1 (the sibling is black and has a red child) is fixed by: (a) recolouring (b) restructuring (c) an adjustment (d) deleting the sibling

**A16.** Splay trees store: (a) heights (b) balance factors (c) colours (d) no extra information

**A17.** If x's parent is the root, the splay step is: (a) zig (b) zig-zig (c) zig-zag (d) none

**A18.** Java's TreeMap and TreeSet are implemented as: (a) AVL trees (b) red-black trees (c) splay trees (d) hash tables

---

## Part B. MCQ Level II (scenarios)

**B1.** A real-time stock trading app needs efficient searching and updating, and **quick access to frequently queried stocks**. Which self-balancing BST? (a) AVL (b) red-black (c) splay tree (d) plain BST *(instructor's sample question)*

**B2.** A dictionary is built once and then searched millions of times with almost no updates. Which tree gives the shortest searches? (a) AVL (b) red-black (c) splay (d) plain BST

**B3.** A system does very many insertions and deletions and needs a guaranteed O(log n) worst case with few rotations. Choose: (a) AVL (b) red-black (c) splay (d) plain BST

**B4.** Keys arrive **already sorted** and are inserted into a plain BST. Searches will be: (a) O(1) (b) O(log n) (c) O(n) (d) O(n log n)

**B5.** You must always guarantee O(log n) per request (a hard real-time limit). Which is **unsuitable**? (a) AVL (b) red-black (c) splay tree (d) (2,4) tree

**B6.** You need to print all keys between 100 and 200 in order, efficiently. Best structure? (a) hash table (b) balanced BST or sorted array (c) min-heap (d) unsorted list

**B7.** A database index lives on disk and you want as few disk reads as possible. Choose: (a) binary search tree (b) multi-way tree such as a (2,4) or B-tree (c) splay tree (d) linked list

**B8.** A web cache keeps recently requested pages fast to reach, and the same few pages are asked for again and again. Choose: (a) splay tree (b) AVL (c) unsorted array (d) heap

**B9.** A medical decision tool asks yes/no questions and ends with a diagnosis. Which tree models this? (a) BST (b) decision tree (c) heap (d) red-black tree

**B10.** A calculator must evaluate expressions such as (2 × (a − 1)) + (3 × b). Which tree and traversal? (a) BST, inorder (b) expression tree, postorder (c) heap, preorder (d) AVL, inorder

---

## Part C. Short answer Level I

C1. The height of a tree is the maximum ______ of any node.
C2. In a proper binary tree, n = ______ e − 1.
C3. Bounds on the height of a proper binary tree: ______ ≤ h ≤ ______.
C4. An Euler tour visits each internal node ______ times.
C5. Binary search on a sorted map takes ______.
C6. Worst-case time of find in a BST with n keys: ______.
C7. Minimum number of keys of an AVL tree of height h: n(h) > ______.
C8. Height of an AVL tree with n keys: ______.
C9. Time of one AVL restructure (trinode) operation: ______.
C10. A multi-way search tree node with d children stores ______ keys.
C11. A (2,4) tree node with 3 children is called a ______.
C12. The (2,4) property requiring all external nodes at the same depth is the ______ property.
C13. The height of a red-black tree is at most ______ times the height of its (2,4) tree.
C14. Worst-case time of insertion and deletion in a red-black tree: ______.
C15. In red-black deletion, if the removed node v or its replacement r is red, you colour r ______.
C16. Red-black deletion Case 3 (the sibling is red) is handled by an ______, after which Case 1 or 2 applies.
C17. On deletion, a splay tree splays the ______ of the removed node.
C18. Average and worst-case running times of splay tree operations: ______ and ______.
C19. The slides mark ______ trees as optional and not in the exam.
C20. TreeSet in Java is implemented on top of ______.

---

## Part D. Short answer Level II (hands-on)

**D1.** Insert 8, 3, 10, 1, 6, 14, 4, 7, 13 into an empty BST. Give the preorder, inorder and postorder traversals.

**D2.** In the D1 tree, delete 3, then 10, then 8. Give the tree after each deletion.

**D3.** Draw the expression tree for (6 × (8 − 3)) + (12 / 4). Give the preorder and postorder traversals and the value.

**D4.** A proper binary tree has 10 internal nodes. How many external nodes and total nodes does it have? What are the minimum and maximum heights?

**D5.** Using binary search on `0 1 3 4 5 7 8 9 11 14 16 18 19`, list the keys in the range [5, 14]. Why is this O(log n + s), where s is the number of keys reported?

**D6.** Insert 40, 20, 10, 25, 30, 22, 50 into an empty AVL tree. Name each rotation and give the final preorder.

**D7.** Insert 5, 10, 15, 20, 25, 30, 35 into an empty AVL tree. Name each rotation and give the final tree.

**D8.** Insert 60, 50, 70, 40, 55, 45 into an empty AVL tree. Which rotation does 45 cause? Give the final tree.

**D9.** (Slide example) Insert 54 into the AVL tree `44[17[-,32],78[50[48,62],88]]`. Give z, y, x and the result. Then delete 32 and give the result.

**D10.** AVL tree `40[20[10[5,-],30[25,35]],60[50,70[65,-]]]`. Delete 50, then 70. Give the tree after each step.

**D11.** AVL tree `50[25[10[5[1,-],15],30[27,-]],75[60,80]]`. Delete 15. Give the result and its preorder.

**D12.** Is `10[5[2,-],20[15,30[25,40[-,50]]]]` an AVL tree? If not, which node is the first unbalanced one from the bottom?

**D13.** (Exam example) Red-black tree `9B[4R[2B,6B[-,7R]],15B[12R,21R]]`. Insert 5 and delete 15. Write the in-order traversal as KEY(colour).

**D14.** Insert 3, 1, 5, 7, 6, 8, 9, 10 into an empty red-black tree. Say what each insertion does and give the final in-order traversal with colours.

**D15.** In the D14 result, delete 7. Name the case and give the in-order traversal with colours. Then delete 1 and 5 and give the final tree.

**D16.** (Slide example) Red-black tree `6B[3R,8R]`. Insert 4, then delete 8. Give the tree after each step.

**D17.** Red-black tree `50B[30R[20B[10R,-],40B],70B[60R,80R]]`. Each part starts from this tree: (a) delete 40, (b) delete 20, (c) delete 30. Name the case and give the in-order traversal with colours.

**D18.** Is `10B[5R[2R,7B],20B]` a valid red-black tree? Which property fails?

**D19.** Convert this (2,4) tree into a red-black tree. Root [10 15 24] with children [2 8], [12], [18], [27 32].

**D20.** (Slide example) Splay tree `6[2[1,4],9[8,-]]`: insert 5. Name the steps and give the result.

**D21.** Starting with an empty splay tree, insert 50, 40, 30, 20 (splaying each time). Then search 50, then search 40. Give the tree after each search.

**D22.** BST `10[5[3,7[6,-]],20[15,25]]` used as a splay tree: search 6. Name the steps and give the result.

**D23.** Splay tree `6[2[1,4],9[8,-]]`: delete 4. Which node is splayed, and what is the result?

**D24.** Give the average and worst-case search, insertion and deletion times for a BST, AVL, red-black and splay tree.

---
---

# Answer key

## Part A
A1 b · A2 c · A3 b · A4 c · A5 b · A6 b · A7 c · A8 b · A9 a · A10 c · A11 b · A12 d · A13 b · A14 b · A15 b · A16 d · A17 a · A18 b

## Part B
- B1 **c**: a splay tree moves frequently queried stocks to the top. If the question stressed a worst-case guarantee, the answer would be red-black.
- B2 **a**: AVL's stricter balance gives a lower tree, so fewer comparisons.
- B3 **b**: red-black needs fewer rotations per update and is still O(log n) worst case.
- B4 **c**: sorted inserts make a chain of height n.
- B5 **c**: a single splay operation can take O(n); it is only O(log n) on average.
- B6 **b**: an ordered structure gives a range query in O(log n + s); a hash table has no order.
- B7 **b**: wide nodes make a shallow tree, so fewer disk blocks are read.
- B8 **a**: recently accessed keys sit near the root.
- B9 **b**: internal nodes are questions and leaves are outcomes.
- B10 **b**: postorder evaluates both subtrees, then applies the operator.

## Part C
C1 depth · C2 2 · C3 log(n + 1) − 1; (n − 1)/2 · C4 three · C5 O(log n) · C6 O(n) · C7 2^(h/2 − 1) · C8 O(log n) · C9 O(1) · C10 d − 1 · C11 3-node · C12 depth · C13 two · C14 O(log n) · C15 black · C16 adjustment · C17 parent · C18 O(log n); O(n) · C19 wavl (weak AVL) · C20 TreeMap

## Part D

**D1.** Tree `8[3[1,6[4,7]],10[-,14[13,-]]]`.
Preorder **8 3 1 6 4 7 10 14 13** · Inorder **1 3 4 6 7 8 10 13 14** · Postorder **1 4 7 6 3 13 14 10 8**

**D2.**
- Delete 3: two children, successor 4 → `8[4[1,6[-,7]],10[-,14[13,-]]]`
- Delete 10: one child → 14 takes its place → `8[4[1,6[-,7]],14[13,-]]`
- Delete 8: successor 13 → `13[4[1,6[-,7]],14]`

**D3.** Tree `+[×[6,−[8,3]],/[12,4]]`.
Preorder **+ × 6 − 8 3 / 12 4** · Postorder **6 8 3 − × 12 4 / +** · Value 6 × 5 + 3 = **33**

**D4.** e = i + 1 = **11**, n = 21. Minimum height ⌈log(22) − 1⌉ = **4**. Maximum height (21 − 1)/2 = **10**.

**D5.** **5 7 8 9 11 14**. Binary search finds the first key ≥ 5 in O(log n), then the s keys are read in order.

**D6.**
- 10: left-left at 40 → **single right rotation** → `20[10,40]`
- 25: no rotation
- 30: 40 unbalanced, left-right → **double rotation** → `20[10,30[25,40]]`
- 22: the root 20 is unbalanced, right-left (20 → 30 → 25) → **double rotation** → `25[20[10,22],30[-,40]]`
- 50: 30 unbalanced, right-right → **single left rotation** → `25[20[10,22],40[30,50]]`

Preorder: **25 20 10 22 40 30 50**

**D7.** Every rotation is a **single left rotation**: at 5 (after 15), at 15 (after 25), at the root 10 (after 30), at 25 (after 35).
Final: **`20[10[5,15],30[25,35]]`**, a perfect tree.

**D8.** 45 goes right of 40. Walking up, 40 and 50 are fine, but 60 is unbalanced (left height 3, right height 1). z = 60, y = 50, x = 40 → left-left → **single right rotation** at 60.
**`50[40[-,45],60[55,70]]`**

**D9.** 54 goes left of 62. The first unbalanced node is **z = 78**, with y = 50 and x = 62 (zig-zag) → **double rotation** → `44[17[-,32],62[50[48,54],78[-,88]]]`.
Delete 32: 17 is fine, 44 is unbalanced. z = 44, y = 62, x = 78 → **single left rotation** → **`62[44[17,50[48,54]],78[-,88]]`**.

**D10.** Delete 50: 60 has left height 0 and right height 2. y = 70, x = 65 (zig-zag) → **double rotation** → `40[20[10[5,-],30[25,35]],65[60,70]]`.
Delete 70: 65 is still balanced → **`40[20[10[5,-],30[25,35]],65[60,-]]`**.

**D11.** Removing 15 leaves 10 with left height 2 (5–1) and right height 0. y = 5, x = 1 → **single right rotation** at 10.
**`50[25[5[1,10],30[27,-]],75[60,80]]`**, preorder **50 25 5 1 10 30 27 75 60 80**.

**D12.** **No.** Going up from the bottom, 40 and 30 are fine (30 has heights 1 and 2). Node **20** has left height 1 (15) and right height 3 (30–40–50), a difference of 2, so it is the first unbalanced node. The root is unbalanced too (2 vs 4).

**D13.** Insert 5: it goes under 6, whose parent is black, so 5 stays red. Delete 15: successor 21 (a red leaf) is copied up and removed.
**2(B) − 4(R) − 5(R) − 6(B) − 7(R) − 9(B) − 12(R) − 21(B)**

**D14.**
- 1, 5: red children of the black root.
- 7: double red under 5; the uncle 1 is red → **recolour** (1 and 5 black; the root stays black).
- 6: double red (7 under 5 is red); the uncle is black → **restructure** 5, 6, 7 → `6B[5R,7R]`.
- 8: the uncle 5 is red → **recolour** (5 and 7 black, 6 red).
- 9: the uncle is black → **restructure** 7, 8, 9 → `8B[7R,9R]`.
- 10: the uncle 7 is red → **recolour** (7 and 9 black, 8 red). Now 8 and its parent 6 are both red, and 8's uncle 1 is black → **restructure** 3, 6, 8 → 6 becomes the black root.

Final `6B[3R[1B,5B],8R[7B,9B[-,10R]]]` → **1(B) − 3(R) − 5(B) − 6(B) − 7(B) − 8(R) − 9(B) − 10(R)**

**D15.** Delete 7: a black leaf, so double black. The sibling 9 is black with red child 10 → **Case 1 restructure** on 8, 9, 10. 9 takes 8's colour (red), 8 and 10 become black.
`6B[3R[1B,5B],9R[8B,10B]]` → **1(B) − 3(R) − 5(B) − 6(B) − 8(B) − 9(R) − 10(B)**
Delete 1: the sibling 5 is black with black children → **Case 2 recolour**: 5 becomes red; the parent 3 was red, so it becomes black. Delete 5: a red leaf, just remove it.
Final **`6B[3B,9R[8B,10B]]`**.

**D16.** Insert 4: it goes right of 3; the uncle 8 is red → **recolour** → `6B[3B[-,4R],8B]`.
Delete 8: a black leaf, so double black. The sibling 3 is black with red child 4 → **Case 1 restructure** → **`4B[3B,6B]`**.

**D17.**
- (a) Delete 40: double black. The sibling 20 is black with red child 10 → **Case 1** → `20R[10B,30B]`.
  **10(B) − 20(R) − 30(B) − 50(B) − 60(R) − 70(B) − 80(R)**
- (b) Delete 20: its child 10 is red → 10 replaces it and is coloured **black**.
  **10(B) − 30(R) − 40(B) − 50(B) − 60(R) − 70(B) − 80(R)**
- (c) Delete 30: successor 40 is copied up and the black leaf is removed → double black. The sibling 20 is black with red child 10 → **Case 1** → `20R[10B,40B]`.
  **10(B) − 20(R) − 40(B) − 50(B) − 60(R) − 70(B) − 80(R)**

**D18.** **No.** 5 is red and its child 2 is also red, which breaks the **internal property**.

**D19.**
- 4-node [10 15 24] → black 15 with red children 10 and 24.
- 3-node [2 8] → black 2 with red right child 8 (or black 8 with red left child 2).
- 2-nodes 12 and 18 → black.
- 3-node [27 32] → black 27 with red right child 32.

Result: **`15B[10R[2B[-,8R],12B],24R[18B,27B[-,32R]]]`**. Every leaf has black depth 3, and no red node has a red child.

**D20.** 5 becomes the **right** child of 4, and 4 is the **right** child of 2 → **zig-zig** (5 rises above 4 and 2, as 6's left child). Then 5's parent is the root 6 → **zig**.
**`5[4[2[1,-],-],6[-,9[8,-]]]`**

**D21.** Each insert lands as the left child of the root → **zig** → after 20: `20[-,30[-,40[-,50]]]`.
Search 50: 50, 40 and 30 are all right children → **zig-zig**, then **zig** → **`50[20[-,40[30,-]],-]`**.
Search 40: 40 is the right child of 20, which is the left child of 50 → **zig-zag** → **`40[20[-,30],50]`**.

**D22.** 6 is the left child of 7, and 7 is the right child of 5 → **zig-zag** → `6[5[3,-],7]` under 10. Then **zig** with the root.
**`6[5[3,-],10[7,20[15,25]]]`**

**D23.** 4 is a leaf, so it is removed directly and its **parent 2** is splayed. 2 is a child of the root → **zig**.
**`2[1,6[-,9[8,-]]]`**

**D24.**

| Tree | Average | Worst |
|---|---|---|
| BST | O(log n) | O(n) |
| AVL | O(log n) | O(log n) |
| Red-black | O(log n) | O(log n) |
| Splay | O(log n) | O(n) |

The same for search, insertion and deletion.
