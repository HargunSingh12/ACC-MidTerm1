# Chapter 3: Search Trees

COMP 8547 Advanced Computing Concepts, Mid-Term I (Friday 23 October 2026). This page covers **only Chapter 3**: binary trees, binary search, BSTs, AVL trees, multi-way and (2,4) trees, red-black trees and splay trees. Everything comes from the Chapter 3 slides. Practice questions are in [questions.md](questions.md).

This chapter supplies most of the hands-on Level II exam questions (insert/delete in red-black, AVL and splay trees), so practise the traces until they feel automatic.

**On this page**
1. [Trees and binary trees](#1-trees-and-binary-trees)
2. [Traversals](#2-traversals)
3. [Sorted maps and binary search](#3-sorted-maps-and-binary-search)
4. [Binary search trees](#4-binary-search-trees)
5. [AVL trees](#5-avl-trees)
6. [Multi-way search trees and (2,4) trees](#6-multi-way-search-trees-and-24-trees)
7. [Red-black trees](#7-red-black-trees)
8. [Splay trees](#8-splay-trees)
9. [wavl trees (not in the exam)](#9-wavl-trees-not-in-the-exam)
10. [Comparison and Java](#10-comparison-and-java)
11. [Last-minute checklist](#11-last-minute-checklist)

---

## 1. Trees and binary trees

**Terminology** (rooted trees):
- **Root:** the node without a parent.
- **Internal node:** has at least one child.
- **External node (leaf):** has no children.
- **Ancestors / descendants:** parent, grandparent, … / child, grandchild, ….
- **Depth:** a node's number of ancestors.
- **Height:** the maximum depth of any node.
- **Subtree:** a node plus all its descendants.

**Binary tree:** each internal node has at most two children, an ordered pair (left, right). In a **proper** binary tree every internal node has exactly two.

Uses:
- **Arithmetic expression trees:** internal nodes are operators, external nodes are operands. Example: ((2 × (a − 1)) + (3 × b)).
- **Decision trees:** internal nodes are yes/no questions, external nodes are outcomes. The slides' example: "Want a fast meal?" leads to McDonald's, Tim's, The Keg or Chalet.

### Properties of proper binary trees
With n nodes, e external nodes, i internal nodes and height h:

| Property | |
|---|---|
| n = e + i | |
| **e = i + 1** | |
| **n = 2e − 1** | |
| h + 1 ≤ e ≤ 2ʰ | |
| h ≤ i ≤ 2ʰ − 1 | |
| **log(n + 1) − 1 ≤ h ≤ (n − 1)/2** | |

## 2. Traversals

| Traversal | Order | Typical use |
|---|---|---|
| **Preorder** | node, left, right | copying a tree, prefix notation |
| **Inorder** | left, node, right | **printing an arithmetic expression**; on a BST it gives **sorted order**; drawing a tree (x = inorder rank, y = depth) |
| **Postorder** | left, right, node | **evaluating an arithmetic expression** (evalExpr) |
| **Euler tour** | walk around the tree | visits each internal node **3 times** (left, below, right) and each external node once |

```
Algorithm evalExpr(v)
  if isExternal(v) then return v.element()
  x ← evalExpr(left(v))
  y ← evalExpr(right(v))
  ◊ ← operator stored at v
  return x ◊ y
```

## 3. Sorted maps and binary search

On an array sorted by key, binary search does find(k) in **O(log n)**. It can be adapted to find all entries with key k, or all keys in a range, in O(log n) plus the output.

Slide example, find(7) on `0 1 3 4 5 7 8 9 11 14 16 18 19`: mid = 8 → go left, mid = 3 → go right, mid = 5 → go right, low = mid = high = 7 → found.

## 4. Binary search trees

A **BST** stores keys at internal nodes so that for u in v's left subtree and w in v's right subtree: **key(u) ≤ key(v) ≤ key(w)**. External nodes store nothing, so a BST is a proper binary tree. **An inorder traversal visits the keys in increasing order.** A BST implements a sorted map.

**Search:** compare with key(v), then go left or right; reaching an external node means not found.

**Insert:** search for k. If it is not found, insert at the leaf w where the search ended. If k already exists, keep searching in the left child and insert there.

**Delete:**
- **Case 1, v has a leaf child w:** remove v and w with `removeExternal(w)`. v's other child takes v's place.
- **Case 2, both of v's children are internal:** find w, the node **after v in inorder order** (the leftmost node of v's right subtree, the *inorder successor*). Copy key(w) into v, then remove w and its leaf child z.

**Performance** with n entries and height h:
- Space O(n).
- find, insert and remove take **O(h)**.
- h is **O(n) worst case** (sorted inserts make a chain) and O(log n) best case.
- Average: random keys give average depth O(log n), but there is no proof that a mix of inserts and deletes stays O(log n).

## 5. AVL trees

> An **AVL tree** is a BST where, for every internal node, the heights of its two children **differ by at most 1**. It is named after Adel'son-Vel'ski and Landis.

- Minimum number of keys of an AVL tree of height h: **n(h) > 2^(h/2 − 1)**.
- So the height is **O(log n)**. Search works as in a BST.

### Insertion
1. Insert as in a BST.
2. Walk up from the new node w towards the root, checking the balance of every node.
3. At the first unbalanced node z, let **y** be its child on the path and **x** its grandchild on the path. Do **restructure(x)** (trinode restructuring): put a, b, c = x, y, z in inorder order, make **b** the subtree root with **a** and **c** as its children, and reattach the four subtrees T0–T3 in order.
   - Same direction (left-left or right-right) → **single rotation** about the middle node.
   - Zig-zag (left-right or right-left) → **double rotation**.
4. **One restructure rebalances the whole tree.** The stored heights must also be updated.

Slide example: inserting 54 into `44[17[-,32],78[50[48,62],88]]` makes 78 unbalanced. z = 78, y = 50, x = 62 → double rotation → `44[17[-,32],62[50[48,54],78[-,88]]]`.

### Deletion
1. Delete as in a BST. Let w be the parent of the removed node.
2. Walk up from w. At the first unbalanced node z, let **y = the taller child of z** and **x = the taller child of y** (on a tie, choose the child on the same side as y, which gives a single rotation).
3. Do restructure(x).
4. **This can unbalance a node higher up, so keep checking all the way to the root.**

Slide example: removing 32 from `44[17[-,32],62[50[48,54],78[-,88]]]` unbalances 44. z = 44, y = 62, x = 78 (single rotation) → `62[44[17,50[48,54]],78[-,88]]`.

### Performance
- One restructure: **O(1)** with a linked structure.
- find **O(log n)**; insert **O(log n)**; remove **O(log n)** (the search plus the restructures up the tree).

## 6. Multi-way search trees and (2,4) trees

**Multi-way search tree:**
- Each internal node has d ≥ 2 children and stores **d − 1 keys** k₁ < … < k_(d−1).
- Keys in child v₁ are < k₁; keys in child vᵢ are between k_(i−1) and kᵢ; keys in the last child are > k_(d−1).
- An inorder traversal visits the keys in increasing order. Height O(log n) when balanced.

**(2,4) tree** (also called 2-4 or 2-3-4 tree):
- **Node-size property:** every internal node has **at most 4 children**.
- **Depth property:** **all external nodes have the same depth**.
- Nodes with 2, 3 or 4 children are **2-nodes, 3-nodes and 4-nodes**.
- Height **O(log n)**, so search is O(log n).

B-trees extend the same idea to disk blocks, for databases and file systems.

## 7. Red-black trees

A **red-black tree** is a BST with these four properties:
1. **Root property:** the root is black.
2. **External property:** every leaf (external node) is black.
3. **Internal property:** the children of a red node are black, so there are no two reds in a row.
4. **Depth property:** all leaves have the same **black depth**.

**Link to (2,4) trees:** a (2,4) tree converts directly into a red-black tree.
- 2-node → a black node.
- 3-node [a b] → a black node with one red child (two shapes are possible).
- 4-node [a b c] → black b with red children a and c.

The height of a red-black tree is **at most twice** the height of its (2,4) tree, so it is **O(log n)**.

### Insertion
Insert as in a BST and colour the new node z **red** (black if it is the root). This keeps the root, external and depth properties. If z's parent v is black, you are done. If v is red, there is a **double red**. Look at z's **uncle** u (v's sibling):

| Uncle u | Fix | Result |
|---|---|---|
| **Black** (or a leaf) | **Restructure**: trinode on z, v and the grandparent. The middle key becomes the subtree root, coloured **black**; the other two are **red** | Done |
| **Red** | **Recolour**: v and u become black, the grandparent becomes red (unless it is the root) | The double red may move up to the grandparent; repeat |

Slide example: inserting 4 into `6B[3R,8R]` puts 4 under 3. The uncle 8 is red → recolour 3 and 8 black; 6 is the root, so it stays black.

### Deletion
Run BST deletion. Let **v** be the internal node removed, **w** the external node removed, and **r** w's sibling (the node that takes v's place).
- **If v or r was red:** colour r black. Done.
- **Otherwise** r becomes **double black**, which breaks the depth property. Let x be r's parent and y r's sibling:

| Case | Situation | Fix |
|---|---|---|
| **1** | y is **black and has a red child** z | **Restructure** (trinode on z, y, x). The new middle takes x's old colour, its two children become black. **Done** |
| **2** | y is **black and both its children are black** | **Recolour**: y becomes red. If x was red it becomes black and you are done; otherwise x becomes double black and the problem **moves up** |
| **3** | y is **red** | **Adjustment**: rotate y above x and swap their colours. Then Case 1 or 2 applies |

Slide example: deleting 8 from `6B[3B[-,4R],8B]` makes a double black. Its sibling 3 is black with red child 4 → Case 1 → `4B[3B,6B]`.

**Performance:** search, insertion and deletion are all **O(log n)** worst case.

### The exam's example, solved
Starting tree: `9B[4R[2B,6B[-,7R]],15B[12R,21R]]`. Insert 5, delete 15, then give the in-order traversal.
- **Insert 5:** it goes left of 6. Its parent 6 is black, so 5 stays red and nothing else changes.
- **Delete 15:** it has two children. Copy its successor 21 into the node, then remove the red leaf 21. No fix-up is needed.
- **Answer:** **2(B) − 4(R) − 5(R) − 6(B) − 7(R) − 9(B) − 12(R) − 21(B)**

## 8. Splay trees

- A splay tree is a BST that **stores no height, balance or colour information**.
- **Splaying** moves the bottom-most node touched by a search, insertion or deletion up to the root, so frequently used keys stay near the top.
- **Search, insert and delete are O(log n) average (amortized), but O(n) worst case**, the same worst case as a plain BST. In practice they perform very well.

### The three splaying steps (x is the node, y its parent, z its grandparent)

| Step | When | What happens |
|---|---|---|
| **zig** | y is the root (x has no grandparent) | one rotation of x over y |
| **zig-zig** | x and y are both left children (or both right) | rotate y over z first, then x over y |
| **zig-zag** | x is a left child and y a right child (or the reverse) | rotate x over y, then x over z |

Repeat until x is the root.

### Which node to splay

| Operation | Node splayed |
|---|---|
| Search for k found at x | **x** (if k is not found, the last node reached) |
| Insert k | the **new node** holding k |
| Delete k from node w | the **parent of w**, i.e. of the node actually removed |

Slide example: inserting 5 into `6[2[1,4],9[8,-]]` puts 5 under 4. The steps are zig-zig, then zig, giving `5[4[2[1,-],-],6[-,9[8,-]]]`.

## 9. wavl trees (not in the exam)

The slides say "optional – not in exam". For context only: a weak AVL tree gives every node a rank, rank differences are 1 or 2, it combines features of AVL and red-black trees, has height at most 2 log(n + 1), and all operations are O(log n).

## 10. Comparison and Java

| Tree | Search (avg) | Insert (avg) | Delete (avg) | Search (worst) | Insert (worst) | Delete (worst) |
|---|---|---|---|---|---|---|
| BST | O(log n)* | O(log n)* | O(log n)* | O(n) | O(n) | O(n) |
| AVL | O(log n) | O(log n) | O(log n) | O(log n) | O(log n) | O(log n) |
| Red-black | O(log n) | O(log n) | O(log n) | O(log n) | O(log n) | O(log n) |
| wavl | O(log n) | O(log n) | O(log n) | O(log n) | O(log n) | O(log n) |
| Splay | O(log n) | O(log n) | O(log n) | O(n) | O(n) | O(n) |

\* For random insertions and deletions of n keys.

**Java:** `TreeMap` and `TreeSet` (Java 8) implement **red-black trees**; TreeSet is built on TreeMap.

**When to use which:**
- **AVL:** lookup-heavy data, because its stricter balance gives a lower tree.
- **Red-black:** update-heavy data, because it does fewer rotations. Used by Java TreeMap, C++ std::map and the Linux scheduler.
- **Splay:** skewed access where a few keys are hot, such as caches. This is the answer to the slides' stock-trading question about "quick access to frequently queried stocks".
- **(2,4) / B-trees:** disk-based indexes.

## 11. Last-minute checklist

- [ ] Depth, height, internal/external nodes; e = i + 1 and n = 2e − 1 for proper binary trees
- [ ] Preorder, inorder and postorder by hand; postorder evaluates an expression and inorder prints it
- [ ] BST delete with the inorder successor
- [ ] AVL: find z, y, x; single vs double rotation; one fix on insert, possibly many on delete
- [ ] (2,4): node-size and depth properties; converting 2-, 3- and 4-nodes to red-black
- [ ] Red-black: the four properties; insert (black uncle → restructure, red uncle → recolour)
- [ ] Red-black delete: Cases 1, 2 and 3
- [ ] Splay: zig, zig-zig, zig-zag, and which node is splayed for search, insert and delete
- [ ] Comparison table, and Java TreeMap = red-black
- [ ] Write KEY(colour) in-order answers exactly in the requested format
