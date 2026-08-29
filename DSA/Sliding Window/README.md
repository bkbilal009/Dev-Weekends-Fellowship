# Sliding Window Technique 

A complete beginner-friendly guide to the **Sliding Window technique in DSA**, from zero to advanced level.
   
The goal of this README is to understand:

* What Sliding Window is
* Why we use it
* How it works
* Fixed-size Sliding Window
* Variable-size Sliding Window
* `left` and `right` pointers
* `if` vs `while`
* How to maintain a window
* Brute Force vs optimized solutions
* How to identify Sliding Window problems
* Common patterns
* Common mistakes
* C++ templates
* Practice problems

---

# 1. What is Sliding Window?

**Sliding Window** is a technique used to solve problems involving a **continuous part of an array or string**.

A continuous part is also called:

* Subarray in an array
* Substring in a string

The main idea is:

> Instead of calculating every subarray or substring from the beginning, we keep one window and move it using two pointers.

Usually, we use:

```text
left
right
```

The window looks like this:

```text
[ 2  4  1  7  3  6  5 ]
  ↑              ↑
 left           right
```

The elements between `left` and `right` are our current window.

---

# 2. Why Do We Need Sliding Window?

Consider this array:

```text
[2, 4, 1, 7, 3, 6, 5]
```

Suppose we want to find the maximum sum of a subarray of size `3`.

The possible windows are:

```text
[2, 4, 1] = 7

[4, 1, 7] = 12

[1, 7, 3] = 11

[7, 3, 6] = 16

[3, 6, 5] = 14
```

The answer is:

```text
16
```

## Brute Force

In brute force, we calculate every window again.

For example:

```text
[2, 4, 1]
```

Then:

```text
[4, 1, 7]
```

Then:

```text
[1, 7, 3]
```

We are doing repeated work.

But look carefully.

Previous window:

```text
[2, 4, 1]
```

Next window:

```text
[4, 1, 7]
```

Only two things changed:

```text
2 went OUT
7 came IN
```

So instead of calculating the complete sum again:

```text
2 + 4 + 1
```

we can simply do:

```text
old sum - 2 + 7
```

This is the main idea of Sliding Window.

---

# 3. Brute Force vs Sliding Window

Suppose:

```text
n = 1,000,000
k = 500,000
```

A brute force solution may repeatedly process many elements.

Its complexity can become:

```text
O(n * k)
```

Sliding Window avoids this repeated work.

We add the new element and remove the old element.

Therefore, many Sliding Window problems can be solved in:

```text
O(n)
```

This is one of the biggest advantages of the technique.

---

# 4. Two Main Types of Sliding Window

There are two major types:

```text
1. Fixed Size Sliding Window
2. Variable Size Sliding Window
```

---

# 5. Fixed Size Sliding Window

A Fixed Size Window means:

> The size of the window is always fixed.

For example:

```text
k = 3
```

Our window must always contain `3` elements.

Array:

```text
[2, 4, 1, 7, 3, 6, 5]
```

The windows will be:

```text
[2, 4, 1]

   [4, 1, 7]

      [1, 7, 3]

         [7, 3, 6]

            [3, 6, 5]
```

The window size is always:

```text
3
```

---

# 6. Fixed Window Example

## Problem

Given:

```text
arr = [2, 4, 1, 7, 3, 6, 5]
k = 3
```

Find the maximum sum of a subarray of size `k`.

---

## Step 1

Start with:

```text
left = 0
right = 0
sum = 0
answer = 0
```

Add:

```text
arr[right]
```

So:

```text
sum = 2
```

Window:

```text
[2]
 ↑
```

Window size:

```text
1
```

We need:

```text
3
```

So continue.

---

## Step 2

Move `right`.

Window:

```text
[2, 4]
 ↑     ↑
left  right
```

Sum:

```text
2 + 4 = 6
```

Window size:

```text
2
```

Still less than `3`.

Continue.

---

## Step 3

Add `1`.

```text
[2, 4, 1]
 ↑        ↑
left    right
```

Sum:

```text
2 + 4 + 1 = 7
```

Window size:

```text
3
```

Now the window is complete.

Update answer:

```text
answer = 7
```

Now slide the window.

Remove the left element:

```text
sum = 7 - 2
sum = 5
```

Move `left`:

```text
left++
```

Now the next window can be formed.

---

## Step 4

Add `7`.

Current window:

```text
[4, 1, 7]
 ↑        ↑
left    right
```

Sum:

```text
5 + 7 = 12
```

Answer:

```text
max(7, 12) = 12
```

Remove `4`:

```text
sum = 12 - 4
sum = 8
```

Move:

```text
left++
```

---

## Step 5

Add `3`.

Window:

```text
[1, 7, 3]
```

Sum:

```text
8 + 3 = 11
```

Answer:

```text
max(12, 11) = 12
```

Remove `1`.

```text
sum = 11 - 1
sum = 10
```

Move `left`.

---

## Step 6

Add `6`.

Window:

```text
[7, 3, 6]
```

Sum:

```text
10 + 6 = 16
```

Answer:

```text
16
```

Remove `7`:

```text
sum = 16 - 7
sum = 9
```

---

## Step 7

Add `5`.

Window:

```text
[3, 6, 5]
```

Sum:

```text
9 + 5 = 14
```

Answer:

```text
max(16, 14) = 16
```

Final answer:

```text
16
```

---

# 7. C++ Code: Maximum Sum Subarray of Size K

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int maxSumSubarray(vector<int>& arr, int k) {

    int left = 0;
    int sum = 0;
    int answer = 0;

    for (int right = 0; right < arr.size(); right++) {

        // Add the current element
        sum += arr[right];

        // Check if window size is k
        if (right - left + 1 == k) {

            // Update answer
            answer = max(answer, sum);

            // Remove the left element
            sum -= arr[left];

            // Move left pointer
            left++;
        }
    }

    return answer;
}

int main() {

    vector<int> arr = {2, 4, 1, 7, 3, 6, 5};

    int k = 3;

    cout << maxSumSubarray(arr, k);

    return 0;
}
```

Output:

```text
16
```

---

# 8. Understanding `left` and `right`

The two pointers control our window.

```text
left  -> beginning of window
right -> end of window
```

Example:

```text
[2, 4, 1, 7, 3, 6, 5]
 ↑           ↑
left        right
```

Everything between them belongs to the current window.

---

# 9. How to Calculate Window Size?

This is very important.

The formula is:

```cpp
right - left + 1
```

Why `+1`?

Suppose:

```text
left = 2
right = 4
```

The indices are:

```text
2, 3, 4
```

There are `3` elements.

Formula:

```text
4 - 2 + 1 = 3
```

Therefore:

```cpp
right - left + 1
```

is the correct window-size formula.

---

# 10. Fixed Window Master Template

A common Fixed Window template looks like this:

```cpp
int left = 0;

for (int right = 0; right < n; right++) {

    // Add arr[right]

    if (right - left + 1 == k) {

        // Calculate/update answer

        // Remove arr[left]

        left++;
    }
}
```

Remember:

```text
RIGHT moves forward
LEFT follows RIGHT
Window size remains K
```

---

# 11. Variable Size Sliding Window

Now let's move to the second major type.

In a Variable Size Window:

> The window size is not fixed.

The window can:

```text
expand
expand
expand
shrink
shrink
expand
```

depending on the condition.

---

# 12. Example: Minimum Size Subarray Sum

Suppose:

```text
arr = [2, 3, 1, 2, 4, 3]
target = 7
```

We need:

> Find the minimum length subarray whose sum is at least `7`.

Notice something important.

The question does NOT say:

```text
k = 3
```

Instead, it gives us a condition:

```text
sum >= 7
```

Therefore, the window size can change.

This is a Variable Sliding Window problem.

---

# 13. Variable Window: Expand

Start:

```text
left = 0
```

Move `right`.

First:

```text
[2]
```

Sum:

```text
2
```

Condition:

```text
2 >= 7
```

False.

Expand.

```text
[2, 3]
```

Sum:

```text
5
```

Still:

```text
5 < 7
```

Expand again.

```text
[2, 3, 1]
```

Sum:

```text
6
```

Still less than `7`.

Expand again.

```text
[2, 3, 1, 2]
```

Sum:

```text
8
```

Now:

```text
8 >= 7
```

The condition is satisfied.

---

# 14. Variable Window: Shrink

Now we want the **minimum** length.

So we try to make the window smaller.

Current:

```text
[2, 3, 1, 2]
```

Length:

```text
4
```

Remove `2`.

```text
[3, 1, 2]
```

Sum:

```text
6
```

Now:

```text
6 >= 7
```

is false.

So we stop shrinking.

Then `right` moves forward again.

This process continues.

---

# 15. Why Do We Use `while`?

This is one of the most important ideas in Variable Sliding Window.

Suppose our condition is:

```cpp
sum >= target
```

We may need to remove multiple elements.

Therefore:

```cpp
while (sum >= target)
```

is useful.

Example:

```text
[1, 2, 3, 4, 5]
```

Sum:

```text
15
```

Target:

```text
7
```

Condition is true.

We can shrink:

```text
[1, 2, 3, 4, 5]
```

then:

```text
[2, 3, 4, 5]
```

then:

```text
[3, 4, 5]
```

then:

```text
[4, 5]
```

We continue shrinking while the condition remains true.

This is why Variable Sliding Window often uses:

```cpp
while
```

---

# 16. Variable Window Master Template

A common template is:

```cpp
int left = 0;

for (int right = 0; right < n; right++) {

    // Add arr[right]

    while (condition) {

        // Update answer

        // Remove arr[left]

        left++;
    }
}
```

The exact condition depends on the problem.

---

# 17. Fixed vs Variable Window

| Fixed Window           | Variable Window              |
| ---------------------- | ---------------------------- |
| Size is fixed          | Size can change              |
| Usually `k` is given   | Usually a condition is given |
| Example: size `k`      | Example: sum >= target       |
| `if` is commonly used  | `while` is commonly used     |
| Expand and remove once | Expand and shrink repeatedly |

Simple rule:

> If the question gives an exact window size `K`, think about Fixed Sliding Window.

> If the question gives a condition such as longest, shortest, at most, or at least, think about Variable Sliding Window.

---

# 18. Sliding Window on Strings

Sliding Window is also very useful for strings.

Example:

```text
s = "abcabcbb"
```

Problem:

> Find the longest substring without repeating characters.

We need a continuous substring.

Start:

```text
[a]
```

Unique.

Expand:

```text
[ab]
```

Unique.

Expand:

```text
[abc]
```

Unique.

Next:

```text
[abca]
```

Now `a` appears twice.

We need to shrink the window.

```text
[abca]
 ↑  ↑
 L  R
```

Remove from the left:

```text
[bca]
```

Now all characters are unique again.

This is Variable Sliding Window.

---

# 19. What Can We Maintain Inside a Window?

Sliding Window is not only about sums.

We can maintain different information.

## Sum

```cpp
sum += arr[right];
```

Remove:

```cpp
sum -= arr[left];
```

## Count

```cpp
count++;
```

## Frequency

```cpp
freq[s[right]]++;
```

## Hash Map

```cpp
unordered_map<char, int> freq;
```

## Set

```cpp
unordered_set<char> st;
```

## Maximum / Minimum

```cpp
maxValue
minValue
```

## Deque

Advanced problems can use:

```cpp
deque<int> dq;
```

For example:

```text
Sliding Window Maximum
```

---

# 20. How to Identify a Sliding Window Problem?

When reading a problem, ask yourself these questions:

### Question 1

Does the problem involve:

```text
subarray
```

or:

```text
substring
```

?

### Question 2

Does it require a **continuous** section?

### Question 3

Do I need:

```text
longest
shortest
maximum
minimum
```

?

### Question 4

Is there a condition like:

```text
at most K
at least K
exactly K
no more than K
```

?

### Question 5

Can I keep some information about the current window?

For example:

```text
sum
count
frequency
distinct characters
maximum
minimum
```

If the answers look like "yes", Sliding Window may be a good technique.

---

# 21. Important Keywords

These words are strong hints:

```text
subarray
substring
contiguous
continuous
window
longest
shortest
maximum
minimum
at most K
at least K
exactly K
```

Especially:

```text
subarray
substring
contiguous
```

are important signals.

---

# 22. Common Sliding Window Patterns

## Pattern 1: Fixed Size

Examples:

```text
Maximum Sum Subarray of Size K
Average of Subarrays of Size K
Maximum Number of Vowels in a Substring of Size K
First Negative Number in Every Window
```

---

## Pattern 2: Longest Window

Examples:

```text
Longest Substring Without Repeating Characters
Longest Subarray With At Most K Distinct Elements
Fruit Into Baskets
```

---

## Pattern 3: Shortest Window

Examples:

```text
Minimum Size Subarray Sum
Minimum Window Substring
```

---

## Pattern 4: Frequency Map

Examples:

```text
Permutation in String
Find All Anagrams in a String
Longest Repeating Character Replacement
```

---

## Pattern 5: Deque

Advanced examples:

```text
Sliding Window Maximum
Sliding Window Minimum
```

---

# 23. Common Mistakes

## Mistake 1: Forgetting to Remove the Left Element

If you are maintaining a sum:

```cpp
sum -= arr[left];
```

must happen when the left element leaves the window.

Do not only do:

```cpp
left++;
```

because the stored information must also be updated.

---

## Mistake 2: Wrong Window Size

Wrong:

```cpp
right - left
```

Correct:

```cpp
right - left + 1
```

---

## Mistake 3: Confusing `if` and `while`

For a basic Fixed Window:

```cpp
if (right - left + 1 == k)
```

is commonly used.

For a Variable Window:

```cpp
while (condition)
```

is commonly used.

---

## Mistake 4: Forgetting to Move `left`

If you write:

```cpp
while (condition) {
    
}
```

but never change `left`, you may create an infinite loop.

You usually need:

```cpp
left++;
```

inside the shrinking process.

---

## Mistake 5: Updating the Answer at the Wrong Time

You must understand whether the problem wants:

```text
longest
shortest
maximum
minimum
```

and update the answer at the correct point.

---

# 24. Why Can Variable Sliding Window Still Be O(n)?

Consider:

```cpp
for (int right = 0; right < n; right++) {

    while (condition) {
        left++;
    }
}
```

At first, it may look like:

```text
O(n²)
```

because there is a `for` loop and a `while` loop.

But usually it is:

```text
O(n)
```

Why?

Because `right` moves from:

```text
0 → n-1
```

only once.

And `left` also moves forward:

```text
0 → n-1
```

only once.

Neither pointer moves backward.

So total pointer movements are approximately:

```text
n + n
```

which is:

```text
O(2n)
```

We ignore constants:

```text
O(n)
```

---

# 25. Important Mental Model

Remember these two rules:

```text
RIGHT → EXPAND
LEFT  → SHRINK
```

When an element enters:

```text
ADD RIGHT
```

When an element leaves:

```text
REMOVE LEFT
```

Visual:

```text
[ A B C D E F G ]
  ↑           ↑
 left        right
```

Expand:

```text
[ A B C D E F G H ]
  ↑               ↑
 left            right
```

Shrink:

```text
  [ B C D E F G H ]
    ↑             ↑
   left          right
```

---

# 26. Sliding Window Master Templates

## Fixed Size Template

```cpp
int left = 0;

for (int right = 0; right < n; right++) {

    // Add the right element

    if (right - left + 1 == k) {

        // Calculate/update answer

        // Remove the left element

        left++;
    }
}
```

---

## Variable Size Template

```cpp
int left = 0;

for (int right = 0; right < n; right++) {

    // Add the right element

    while (condition) {

        // Calculate/update answer

        // Remove the left element

        left++;
    }
}
```

---

# 27. When NOT to Use Sliding Window

Do not use Sliding Window just because the problem contains an array.

For example:

```text
Two Sum
```

is normally not a standard Sliding Window problem.

Similarly:

```text
Maximum Subarray
```

has a classic solution using **Kadane's Algorithm**.

The important thing is to understand the structure of the problem.

Sliding Window is especially useful when dealing with:

```text
continuous ranges
subarrays
substrings
```

and we can efficiently maintain information about the current window.

---

# 28. Learning Roadmap

A good order for learning Sliding Window is:

```text
LEVEL 1: Beginner
│
├── Maximum Sum Subarray of Size K
├── Average of Subarrays of Size K
└── First Negative Number in Every Window
│
LEVEL 2: Easy / Medium
│
├── Minimum Size Subarray Sum
├── Longest Subarray With a Condition
└── At Most K Distinct Elements
│
LEVEL 3: Strings
│
├── Longest Substring Without Repeating Characters
├── Longest Repeating Character Replacement
├── Find All Anagrams
└── Permutation in String
│
LEVEL 4: Advanced
│
├── Minimum Window Substring
└── Sliding Window Maximum
│
LEVEL 5: Interview Practice
│
└── Mixed Sliding Window Problems
```

---

# 29. Practice Problems

Practice these in this order:

### Easy

1. Maximum Sum Subarray of Size K
2. Average of Subarrays of Size K
3. Maximum Number of Vowels in a Substring of Size K
4. First Negative Number in Every Window

### Medium

5. Minimum Size Subarray Sum
6. Longest Substring Without Repeating Characters
7. Longest Repeating Character Replacement
8. Fruit Into Baskets

### Advanced

9. Permutation in String
10. Minimum Window Substring
11. Sliding Window Maximum
12. Find All Anagrams in a String

---

# 30. Quick Cheat Sheet

```text
                    SLIDING WINDOW
                          |
             +------------+------------+
             |                         |
        FIXED WINDOW             VARIABLE WINDOW
             |                         |
        Size = K                 Size changes
             |                         |
       K is given              Condition is given
             |                         |
       if is common             while is common
             |                         |
      Expand + remove           Expand + shrink
```

Remember:

```text
RIGHT → Expand
LEFT  → Shrink
```

Window size:

```cpp
right - left + 1
```

Fixed Window:

```cpp
if (right - left + 1 == k)
```

Variable Window:

```cpp
while (condition)
```

---

# 31. The Most Important Idea

Do not try to memorize only the code.

Understand this idea:

> **Sliding Window means keeping a continuous range and moving that range efficiently instead of calculating every range from scratch.**

For example:

```text
Old Window:

[2, 4, 1]

New Window:

[4, 1, 7]
```

Instead of recalculating:

```text
4 + 1 + 7
```

we can use the previous result:

```text
old sum - outgoing element + incoming element
```

```text
7 - 2 + 7 = 12
```

That is the heart of Sliding Window.

---

# 32. Final Mental Checklist

Whenever you see a new DSA problem, ask:

```text
1. Is it about an array or string?

2. Does it involve a subarray or substring?

3. Does the range need to be continuous?

4. Is the window size fixed?

5. If not fixed, is there a condition?

6. Can I use left and right pointers?

7. Can I maintain sum/count/frequency/etc.?

8. Can I avoid recalculating the whole window?

9. Can I move left and right only forward?

10. Can this reduce the solution from O(n²) to O(n)?
```

If most answers are yes, **Sliding Window should be one of the first techniques you consider.**

---

# Final Summary

Sliding Window is a powerful DSA technique for working with **continuous ranges of arrays and strings**.

The two most important types are:

```text
Fixed Size Window
Variable Size Window
```

The most important pointers are:

```text
left
right
```

The most important movement is:

```text
right → expand
left  → shrink
```

The most important window-size formula is:

```cpp
right - left + 1
```

The most important Fixed Window condition is:

```cpp
right - left + 1 == k
```

The most important Variable Window idea is:

```cpp
while (condition)
```

And the most important concept to remember is:

> **Do not recalculate what you already know. Reuse the information from the previous window.**

That is what makes Sliding Window so powerful.

---

## 🚀 Next Step

After understanding this README, practice in this order:

```text
1. Maximum Sum Subarray of Size K
2. Average of Subarrays of Size K
3. First Negative Number in Every Window
4. Minimum Size Subarray Sum
5. Longest Substring Without Repeating Characters
6. Longest Repeating Character Replacement
7. Fruit Into Baskets
8. Permutation in String
9. Find All Anagrams in a String
10. Minimum Window Substring
11. Sliding Window Maximum
```

**Master the first 3 problems before moving to Variable Sliding Window. Then move step-by-step toward the advanced problems.**
