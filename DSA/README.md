# 🚀 DevWeekends 8-Week DSA Patterns Mastery

A structured, 8-week pattern-based roadmap designed to master Data Structures and Algorithms using **C++**. This curriculum focuses on mastering **22 core algorithmic patterns** (Two Pointers, Sliding Window, Binary Search, Graph Traversals, DP) rather than brute-force memorization.

---

## 🌐 Connect & Track My Progress
* **GitHub Profile:** [@bkbilal009](https://github.com/bkbilal009)
* **LinkedIn Professional Network:** [Muhammad Bilal](https://www.linkedin.com/in/muhammad-bilal-dev/)
* **Live Interactive Study Planner:** [My Notion DSA & LeetCode Tracker](https://app.notion.com/p/DSA-Leetcode-Problems-Planner-2f7f30e9279a80739d17eaf4ec6cf35f?source=copy_link)

---

## 🏢 Target Company Pattern Focus & Weightage

Top tech companies heavily lean on specific pattern clusters. Here is the distribution breakdown to prioritize while solving:

* **Google:** Dynamic Programming (25%), Graph Algorithms (20%), Binary Search (15%), Two Pointers / Sliding Window (15%), HashMap / HashSet (10%)
* **Meta (Facebook):** Binary Search (15%), Two Pointers / Sliding Window (15%), Dynamic Programming (15%), HashMaps (15%), Trees & Graphs (20%)
* **Amazon:** Graph Algorithms & Traversals (20%), Two Pointers / Sliding Window (15%), Tree Traversal (15%), Heap / Priority Queue (10%)
* **Microsoft:** HashMap / HashSet (15%), Trees & Graphs (20%), Two Pointers (15%), Arrays & Strings (20%)

---

## 🕒 Daily Routine & Execution Rules
* **Slot 1 (1.5 Hours):** Understand the target pattern logic, constraints, and key trigger words.
* **Slot 2 (1.0 Hour):** Pen-Paper Dry Run — trace variables and write step-by-step logic before coding.
* **Slot 3 (1.5 Hours):** Implement the optimal C++ solution from scratch and solve 2–3 targeted LeetCode problems.

---

## ⚡ 30-Second Pattern Lookup Cheatsheet

| Problem Statement Clues | Reach For Pattern |
| :--- | :--- |
| Sorted array + Find pair with sum X / Two numbers that... | **Two Pointers (Converging)** |
| Remove duplicates in-place / Move zeroes / Cycle detection | **Two Pointers (Fast/Slow)** |
| Contiguous subarray / Substring with max/min/k distinct | **Sliding Window** |
| Range sum query / Subarray sum equals K (with negatives) | **Prefix Sum + HashMap** |
| Find element in sorted/rotated array / Minimize the max | **Binary Search** |
| Shortest path in unweighted graph / Level-by-level traversal | **BFS** |
| All paths / Connected components / Tree path sum | **DFS** |
| Next greater element / Daily temperatures / Stock span | **Monotonic Stack** |
| Top K elements / Merge K sorted streams / Median of stream | **Min/Max Heap** |
| Subsets / Permutations / Combinations / Sudoku solver | **Backtracking** |
| Min coins / Ways to climb stairs / 0-1 Knapsack / LCS | **Dynamic Programming** |

---

## 🗺️ The 8-Week Master Pattern Roadmap

### 🟩 Phase 1: Foundation (Weeks 1–2)
*Goal: Master Two Pointers, Sliding Window, and HashMap (covers ~40% of interview questions)*

- [ ] **Week 1 - Day 1:** Two Pointers Intro (*Two Sum II*, *Valid Palindrome*)
- [ ] **Week 1 - Day 2:** Two Pointers Practice (*3Sum*, *Container With Most Water*)
- [ ] **Week 1 - Day 3:** Fixed Sliding Window (*Max Sum Subarray of Size K*, *Avg of Subarrays*)
- [ ] **Week 1 - Day 4:** Variable Sliding Window (*Longest Substring Without Repeating Characters*)
- [ ] **Week 1 - Day 5:** HashMap Basics (*Two Sum*, *Contains Duplicate*)
- [ ] **Week 1 - Day 6:** HashMap + Frequency (*Valid Anagram*, *Group Anagrams*)
- [ ] **Week 1 - Day 7:** Review & Mixed Practice (3 Random Medium Problems)
- [ ] **Week 2 - Day 8-14:** Fast & Slow Pointers, Prefix Sum + HashMap (*Linked List Cycle*, *Subarray Sum Equals K*)

---

### 🟩 Phase 2: Core Patterns (Weeks 3–4)
*Goal: Master Search Algorithms, Graph Traversals, and Linear Data Structures*

- [ ] **Week 3 - Day 15-18:** Binary Search Variants (Classic BS, BS on Answer, Rotated Array, Pivot Element)
- [ ] **Week 3 - Day 19-21:** Stack & Queue Core (Valid Parentheses, Min Stack, Circular Queue Implementation)
- [ ] **Week 4 - Day 22-25:** Tree & Graph Traversals (BFS Level Order, DFS Pre/In/Postorder, Path Sum, LCA)
- [ ] **Week 4 - Day 26-28:** Monotonic Stack & Deque Patterns (Next Greater Element, Sliding Window Maximum)

---

### 🟨 Phase 3: Intermediate Patterns (Weeks 5–6)
*Goal: Master Search Space Pruning, Greedy Strategy, and Dynamic Programming*

- [ ] **Week 5 - Day 29-32:** Recursion & Backtracking (Subsets, Permutations, Combination Sum, Rat in a Maze)
- [ ] **Week 5 - Day 33-35:** Greedy Strategy (Gas Station, Jump Game, Assign Cookies)
- [ ] **Week 6 - Day 36-39:** Dynamic Programming 1D (Climbing Stairs, House Robber, Coin Change, Unbounded Knapsack)
- [ ] **Week 6 - Day 40-42:** Dynamic Programming 2D (0/1 Knapsack, Longest Common Subsequence, Edit Distance)

---

### 🟦 Phase 4: Advanced Techniques (Weeks 7–8)
*Goal: Master specialized data structures for complex and hard-level problems*

- [ ] **Week 7 - Day 43-46:** Heap & Priority Queue (Top K Frequent Elements, Merge K Sorted Lists, Median of Stream)
- [ ] **Week 7 - Day 47-49:** Disjoint Set Union / Union-Find (Connected Components, Redundant Connection)
- [ ] **Week 8 - Day 50-53:** Trie / Prefix Tree (Implement Trie, Word Search II, Autocomplete Systems)
- [ ] **Week 8 - Day 54-56:** Bit Manipulation & Advanced Review (Single Number, Counting Bits, Mock Interviews)

---

## 🛠️ Getting Unstuck: 6-Step Interview Playbook

When stuck during a problem or interview round, follow this exact playbook:

1. **Restate the problem in one sentence:** Compress the statement (e.g., *"Find the minimum contiguous window containing all required elements"*).
2. **Identify input shape & properties:** Is it sorted? (Unlocks Binary Search/Two Pointers). Contiguous? (Unlocks Sliding Window). Graph/Tree? (Unlocks BFS/DFS).
3. **State the Brute-Force first:** Always explain the naïve $O(N^2)$ or exponential approach out loud to show reasoning and buy thinking time.
4. **Identify Redundancy:** Look for repeated scans or re-computed values (e.g., replace repeated sum calculation with Prefix Sum or Window Shift).
5. **Analyze Constraints:** 
   * $N \le 10^5 \implies O(N)$ or $O(N \log N)$ expected.
   * $N \le 20 \implies O(2^N)$ Backtracking/Pruning is acceptable.
6. **Narrate your thought process:** Never stay silent. Verbally walk through why a candidate pattern fits or fails constraints.

---

## 📝 Rules of Engagement & Strategy Notes
> **The 80/20 Rule:** Focus heavily on the top 6 patterns (Two Pointers, Sliding Window, HashMap, Binary Search, DFS/BFS, and DP). Never jump to code without writing the dry-run steps on paper first!
