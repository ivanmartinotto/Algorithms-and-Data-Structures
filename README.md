# Algorithms and Data Structures — Overview

This repository is a collection of educational Jupyter notebooks that implement classical algorithms and data structures. Each notebook contains code, explanatory notes and small experiments (timings, correctness checks) designed to build intuition about algorithmic complexity, implementation trade-offs and practical behavior on realistic inputs.

Below is a concise overview of every implemented algorithm and what each exercise contributes to general notions of data structures and their importance in computing.

---

## Notebooks and implemented algorithms

1. counting_radix_bucket_tries.ipynb
   - Counting Sort
     - Non-comparison integer sorting using counting/frequency arrays.
     - Demonstrates O(n + k) complexity and when counting sort is preferred (small, bounded key range).
   - Radix Sort (LSD using Counting Sort per digit)
     - Stable, linear-time sorting for fixed-digit keys: O(d · n).
     - Shows how a non-comparison approach scales when keys have bounded digit length.
   - Bucket Sort
     - Sorting real numbers by distribution into buckets, each sorted (here with insertion sort).
     - Teaches the role of data distribution (uniform vs skewed) on average complexity (O(n) for ideal distributions).
   - Trie (digital tree) with binary keys
     - Implements insertion, removal, height computation and printing for binary-coded keys (letters).
     - Demonstrates prefix-based storage, predictable depth bounds, and fast lookup by key bits.

2. shell_quick_merge.ipynb
   - Shellsort (three gap sequences: Shell, Knuth, Sedgwick)
     - Practical improvement over insertion sort by comparing distant elements; experiments show effect of gap sequence on runtime.
     - Teaches importance of sequence selection for empirical performance.
   - Quicksort (Lomuto partition)
     - Classic divide-and-conquer comparison sort with average O(n log n) and worst-case O(n^2).
     - Illustrates pivoting, partition cost and role of input order; timing experiments compare practical speed.
   - Mergesort (linear merge)
     - Stable divide-and-conquer algorithm with guaranteed O(n log n) complexity.
     - Demonstrates external/auxiliary-array merging cost and consistent performance independent of input ordering.

3. skipList_hashTable.ipynb
   - Skip List
     - Probabilistic, layered linked structure providing expected O(log n) search, insert and delete.
     - Shows height/level distribution, path traversal, and the simplicity of probabilistic balancing compared to deterministic balanced trees.
   - Hash Table (linear probing)
     - Open-addressing hash table with insertion, search and display; probes and collisions are measured.
     - Demonstrates constant-time average access, collision resolution trade-offs, load factor impact and memory locality benefits.

4. transaction_management_system.ipynb
   - Balanced search tree (AVL tree) for transaction management
     - Implements AVL insertion, deletion, search and in-order traversal keyed by transaction time.
     - Uses the AVL balancing invariants to guarantee O(log n) operations; includes experiments inserting thousands of random transactions and timed removals.
     - Illustrates how balanced trees support ordered queries (chronological traversals), range deletions and stable worst-case guarantees needed in system-like workloads.

---

## What each work contributes to general notions of data structures

- Complexity reasoning (time and space)
  - By implementing and timing algorithms, you see the practical impact of asymptotic complexity: linear-time non-comparison sorts (Counting/Radix/Bucket) vs. comparison sorts (Quick/Merge/Shell).
- Trade-offs and applicability
  - Different algorithms are optimal for different data shapes: Counting/Radix/Bucket when keys/range/distribution allow; Quicksort and Mergesort for general-purpose sorting; Tries for prefix/pattern lookups; Hash tables for average-case O(1) access; Balanced trees when order and worst-case guarantees matter.
- Deterministic vs probabilistic balancing
  - Skip lists show probabilistic balancing that is simpler to implement than AVL/Red-Black trees, while AVL trees show deterministic balancing required for strict worst-case bounds.
- Stability, memory and locality considerations
  - Mergesort is stable but uses extra memory; Quicksort is in-place (but may degrade on certain inputs); linear probing hash tables benefit from cache locality.
- Implementation details matter
  - Choice of pivot/gap sequence/collision strategy/auxiliary structures dramatically affects empirical performance; small implementation choices (stable counting sort or digit order in radix) change correctness and efficiency.
- Data-structure choice shapes system design
  - For an application (e.g., transaction management), the choice of a balanced tree (AVL) enables efficient chronological queries and deletions; for high-throughput key-value lookup, hashing or skip lists can be more appropriate.
- Experimentation as learning
  - Measuring runtime, tree height, probe counts and other metrics builds intuition beyond theoretical bounds and helps understand constants and caching effects in real environments.

---

## Why these data structures matter for computing

- Performance: choosing the right structure/algorithm yields orders-of-magnitude improvements in speed and memory.
- Predictability: balanced trees and deterministic algorithms provide worst-case guarantees important for real-time and safety-critical systems.
- Scalability: linear or log-time primitives allow systems to scale to large datasets.
- Functionality: different structures provide different capabilities—ordered traversal (trees), prefix search (tries), O(1) average lookup (hash tables), and compact probabilistic alternatives (skip lists).
- Foundations: these structures are building blocks for databases, compilers, networks, search engines and many production systems.

---

## How to run the notebooks

1. Requirements
   - Python 3.7+ and Jupyter or Google Colab. Notebooks use only the Python standard library and numpy/time/random for experiments.
2. Steps
   - Open a notebook (e.g., `shell_quick_merge.ipynb`) in Jupyter or upload to Colab.
   - Execute cells top-to-bottom. Each notebook includes explanatory markdown, the implementation and simple timing/verification cells.
   - Modify input sizes and parameters (array sizes, number of transactions, gap sequences, load factors) to reproduce or extend experiments.

