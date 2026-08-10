# Two Pointer Technique

A complete beginner-friendly guide to the **Two Pointer technique in DSA**, from zero to advanced level.

This README explains:

* What Two Pointer is
* Why we use it
* Brute Force vs Two Pointer
* What pointers mean
* Left and Right pointers
* Same-direction pointers
* Opposite-direction pointers
* How pointers move
* When to move `left`
* When to move `right`
* Two Pointer with sorted arrays
* Two Pointer with strings
* Two Pointer with linked lists
* Fast and Slow pointers
* How to identify Two Pointer problems
* Common patterns
* Common mistakes
* C++ templates
* Practice problems

---

# 1. What is Two Pointer?

**Two Pointer** is a problem-solving technique where we use **two variables/pointers** to keep track of positions in an array, string, linked list, or another data structure.

The pointers are usually called:

```text
left
right
```

For example:

```text
[1, 2, 3, 4, 5, 6, 7]
 ↑                 ↑
left              right
```

Here:

```text
left = 0
right = 6
```

Instead of using nested loops, we move the two pointers intelligently.

The main goal is:

> **Use two pointers to reduce unnecessary work.**

Many problems that look like:

```text
O(n²)
```

can be optimized to:

```text
O(n)
```

using Two Pointer.

---

# 2. Why Do We Need Two Pointer?

Consider this array:

```text
[1, 2, 3, 4, 5, 6]
```

Suppose the problem is:

> Find two numbers whose sum is `7`.

A brute force solution can check every pair.

```text
1 + 2
1 + 3
1 + 4
1 + 5
1 + 6

2 + 3
2 + 4
2 + 5
2 + 6

...
```

This can take:

```text
O(n²)
```

comparisons.

But the array is sorted.

We can use two pointers:

```text
[1, 2, 3, 4, 5, 6]
 ↑                 ↑
left              right
```

Calculate:

```text
1 + 6 = 7
```

We found the answer immediately.

Only a few pointer movements were needed.

This is the power of Two Pointer.

---

# 3. The Core Idea

The most important thing to understand is:

> **Two Pointer means using two positions and moving them based on the problem's condition.**

For example:

```text
[1, 2, 3, 4, 5, 6]
 ↑              ↑
 L              R
```

If:

```text
arr[left] + arr[right] < target
```

we may move:

```text
left++
```

If:

```text
arr[left] + arr[right] > target
```

we may move:

```text
right--
```

Why?

Because the array is sorted.

That gives us useful information about which direction to move.

---

# 4. Two Main Types of Two Pointer

There are two major patterns:

```text
1. Opposite Direction Pointers
2. Same Direction Pointers
```

There is also an important special pattern:

```text
3. Fast and Slow Pointers
```

We will learn all three.

---

# 5. Pattern 1: Opposite Direction Pointers

This is the most common beginner Two Pointer pattern.

We start:

```text
left = 0
right = n - 1
```

Example:

```text
[1, 2, 3, 4, 5, 6]
 ↑                 ↑
left              right
```

Then:

```text
left++
```

moves left pointer to the right.

And:

```text
right--
```

moves right pointer to the left.

So the pointers move toward each other.

Visual:

```text
[1, 2, 3, 4, 5, 6]
 ↑                 ↑
 L                 R

      ↓       ↓

[1, 2, 3, 4, 5, 6]
    ↑           ↑
    L           R

          ↓ ↓

[1, 2, 3, 4, 5, 6]
       ↑     ↑
       L     R
```

Eventually:

```text
left >= right
```

and we stop.

---

# 6. Example: Two Sum in a Sorted Array

## Problem

Given a sorted array:

```text
[1, 2, 3, 4, 6, 8, 9]
```

Find two numbers whose sum is:

```text
target = 10
```

---

# 7. Step-by-Step Dry Run

Start:

```text
[1, 2, 3, 4, 6, 8, 9]
 ↑                    ↑
 L                    R
```

Calculate:

```text
1 + 9 = 10
```

We found the answer.

So:

```text
1 + 9 = 10
```

Answer:

```text
[1, 9]
```

This was easy because the answer happened immediately.

Let's look at a case where we need to move pointers.

---

# 8. Another Example

Array:

```text
[1, 2, 3, 4, 6, 8, 9]
```

Target:

```text
13
```

Start:

```text
[1, 2, 3, 4, 6, 8, 9]
 ↑                    ↑
 L                    R
```

Calculate:

```text
1 + 9 = 10
```

We need:

```text
13
```

Current sum is too small.

So we need a bigger value.

Because the array is sorted:

```text
left++
```

Move left:

```text
[1, 2, 3, 4, 6, 8, 9]
    ↑                 ↑
    L                 R
```

Now:

```text
2 + 9 = 11
```

Still too small.

Move left:

```text
[1, 2, 3, 4, 6, 8, 9]
       ↑              ↑
       L              R
```

Now:

```text
3 + 9 = 12
```

Still too small.

Move left:

```text
[1, 2, 3, 4, 6, 8, 9]
          ↑           ↑
          L           R
```

Now:

```text
4 + 9 = 13
```

Found the answer.

```text
4 + 9 = 13
```

---

# 9. Why Does `left++` Work?

This is the most important reasoning.

Array is sorted:

```text
1 2 3 4 6 8 9
```

Suppose:

```text
1 + 9 = 10
```

Target:

```text
13
```

The sum is too small.

Could we decrease `right`?

No.

If we decrease `right`:

```text
1 + 8 = 9
```

The sum becomes even smaller.

That is not useful.

So we increase `left`.

```text
2 + 9 = 11
```

Then:

```text
3 + 9 = 12
```

Then:

```text
4 + 9 = 13
```

Because the array is sorted, we know exactly which pointer to move.

This is why Two Pointer works so well on sorted arrays.

---

# 10. Three Possible Cases

Suppose:

```text
sum = arr[left] + arr[right]
```

We compare it with target.

## Case 1: Sum is too small

```text
sum < target
```

We need a bigger sum.

Move:

```cpp
left++;
```

---

## Case 2: Sum is too large

```text
sum > target
```

We need a smaller sum.

Move:

```cpp
right--;
```

---

## Case 3: Sum is equal

```text
sum == target
```

We found the answer.

```cpp
return true;
```

So the basic logic is:

```text
sum < target
      ↓
   left++

sum > target
      ↓
   right--

sum == target
      ↓
   answer found
```

---

# 11. C++ Code: Two Sum Sorted Array

```cpp
#include <iostream>
#include <vector>
using namespace std;

bool twoSum(vector<int>& arr, int target) {

    int left = 0;
    int right = arr.size() - 1;

    while (left < right) {

        int sum = arr[left] + arr[right];

        if (sum == target) {
            return true;
        }

        else if (sum < target) {
            left++;
        }

        else {
            right--;
        }
    }

    return false;
}

int main() {

    vector<int> arr = {1, 2, 3, 4, 6, 8, 9};

    int target = 13;

    cout << twoSum(arr, target);

    return 0;
}
```

Output:

```text
1
```

Here:

```text
1 = true
0 = false
```

---

# 12. Complexity

Each pointer moves only forward toward the other pointer.

Therefore:

```text
Time Complexity:
O(n)
```

Extra space:

```text
O(1)
```

This is much better than:

```text
O(n²)
```

brute force.

---

# 13. Pattern 2: Same Direction Pointers

The second pattern is when both pointers move in the same direction.

For example:

```text
left →
right →
```

They do not necessarily start from opposite ends.

Example:

```text
[1, 1, 2, 2, 3, 3]
 ↑  ↑
 L  R
```

Both can move toward the right.

This pattern is very common when:

* Removing duplicates
* Modifying arrays in-place
* Partitioning arrays
* Keeping valid elements
* Comparing ranges

---

# 14. Example: Remove Duplicates from Sorted Array

Array:

```text
[1, 1, 2, 2, 3]
```

We want:

```text
[1, 2, 3]
```

without using another array.

We can use two pointers.

One pointer keeps track of the position where the next unique element should go.

Another pointer scans the array.

Let's call them:

```text
slow
fast
```

Start:

```text
[1, 1, 2, 2, 3]
 ↑  ↑
slow fast
```

The first element is already unique.

Move `fast`.

```text
[1, 1, 2, 2, 3]
 ↑     ↑
slow  fast
```

`1` is duplicate.

So we do not move `slow`.

Move `fast` again.

```text
[1, 1, 2, 2, 3]
 ↑        ↑
slow    fast
```

Now `2` is different from the last unique value.

Move `slow`:

```text
[1, 2, 2, 2, 3]
    ↑
   slow
```

Copy `2`.

Continue.

Eventually:

```text
[1, 2, 3]
```

This is a classic Two Pointer problem.

---

# 15. Fast and Slow Pointers

This is another important Two Pointer pattern.

We use:

```text
slow
fast
```

Usually:

```text
slow moves one step
fast moves two steps
```

For example:

```cpp
slow = slow->next;
fast = fast->next->next;
```

This is extremely useful in linked lists.

---

# 16. Example: Detect Cycle in Linked List

Suppose:

```text
1 → 2 → 3 → 4
        ↑     ↓
        ← ← ←
```

There is a cycle.

Use:

```text
slow
fast
```

Initially:

```text
slow = head
fast = head
```

Every step:

```text
slow → 1 step
fast → 2 steps
```

If there is a cycle, eventually:

```text
slow == fast
```

Therefore, we can detect the cycle.

---

# 17. Floyd's Cycle Detection Algorithm

The basic idea:

```text
slow = slow->next
fast = fast->next->next
```

If:

```text
slow == fast
```

then a cycle exists.

If:

```text
fast == nullptr
```

or:

```text
fast->next == nullptr
```

then there is no cycle.

---

# 18. C++ Code: Linked List Cycle

```cpp
class Solution {
public:

    bool hasCycle(ListNode *head) {

        ListNode* slow = head;
        ListNode* fast = head;

        while (fast != nullptr && fast->next != nullptr) {

            slow = slow->next;

            fast = fast->next->next;

            if (slow == fast) {
                return true;
            }
        }

        return false;
    }
};
```

Time:

```text
O(n)
```

Space:

```text
O(1)
```

---

# 19. Why Does Fast and Slow Work?

Imagine two runners on a circular track.

One runner moves:

```text
1 step
```

The other moves:

```text
2 steps
```

If they are running on a circle, the faster runner will eventually catch the slower runner.

The same idea works in a linked list cycle.

---

# 20. Two Pointer on Strings

Two Pointer can also work on strings.

Example:

```text
"madam"
```

We want to check whether it is a palindrome.

Start:

```text
m a d a m
↑       ↑
L       R
```

Compare:

```text
s[left] == s[right]
```

```text
m == m
```

Good.

Move:

```text
left++
right--
```

Now:

```text
m a d a m
  ↑   ↑
  L   R
```

Compare:

```text
a == a
```

Good.

Move again:

```text
m a d a m
    ↑
   L/R
```

All characters matched.

Therefore:

```text
Palindrome = true
```

---

# 21. C++ Code: Valid Palindrome

```cpp
#include <iostream>
using namespace std;

bool isPalindrome(string s) {

    int left = 0;
    int right = s.length() - 1;

    while (left < right) {

        if (s[left] != s[right]) {
            return false;
        }

        left++;
        right--;
    }

    return true;
}

int main() {

    string s = "madam";

    cout << isPalindrome(s);

    return 0;
}
```

Output:

```text
1
```

---

# 22. Two Pointer vs Sliding Window

These two techniques are related, but they are not exactly the same.

## Two Pointer

Main idea:

```text
Use two positions to reduce unnecessary work.
```

Pointers can move:

```text
toward each other
```

or:

```text
in the same direction
```

Examples:

```text
Two Sum
Palindrome
Remove Duplicates
Cycle Detection
Container With Most Water
```

---

## Sliding Window

Main idea:

```text
Maintain a continuous window.
```

Usually:

```text
left + right
```

define the current window.

Examples:

```text
Maximum Sum Subarray of Size K
Longest Substring Without Repeating Characters
Minimum Window Substring
```

Simple difference:

```text
Two Pointer
    ↓
Two positions/pointers

Sliding Window
    ↓
A continuous range controlled by pointers
```

Sliding Window can actually be considered a specialized use of the Two Pointer idea.

---

# 23. Two Pointer Patterns

A useful classification is:

```text
                    TWO POINTER
                         |
          +--------------+--------------+
          |              |              |
     Opposite        Same Direction   Fast/Slow
     Direction
          |              |              |
      L → ← R          L → R →        Slow → 1
                                       Fast → 2
```

---

# 24. Pattern: Opposite Direction

Typical setup:

```cpp
int left = 0;
int right = n - 1;

while (left < right) {

    // Compare or calculate

    // Move left or right
}
```

Common problems:

```text
Two Sum II
Valid Palindrome
Container With Most Water
3Sum
4Sum
Reverse String
```

---

# 25. Pattern: Same Direction

Typical setup:

```cpp
int slow = 0;

for (int fast = 0; fast < n; fast++) {

    if (condition) {

        // Use slow

        slow++;
    }
}
```

Common problems:

```text
Remove Duplicates
Move Zeroes
Remove Element
Partitioning
```

---

# 26. Pattern: Fast and Slow

Typical setup:

```cpp
slow = slow->next;
fast = fast->next->next;
```

Common problems:

```text
Linked List Cycle
Middle of Linked List
Happy Number
Find Duplicate Number
```

---

# 27. Example: Reverse an Array

Given:

```text
[1, 2, 3, 4, 5]
```

We want:

```text
[5, 4, 3, 2, 1]
```

Start:

```text
[1, 2, 3, 4, 5]
 ↑           ↑
 L           R
```

Swap:

```text
[5, 2, 3, 4, 1]
```

Move:

```text
L++
R--
```

Now:

```text
[5, 2, 3, 4, 1]
    ↑     ↑
    L     R
```

Swap:

```text
[5, 4, 3, 2, 1]
```

Move again.

Eventually:

```text
left >= right
```

Stop.

---

# 28. C++ Code: Reverse Array

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

void reverseArray(vector<int>& arr) {

    int left = 0;
    int right = arr.size() - 1;

    while (left < right) {

        swap(arr[left], arr[right]);

        left++;
        right--;
    }
}

int main() {

    vector<int> arr = {1, 2, 3, 4, 5};

    reverseArray(arr);

    for (int x : arr) {
        cout << x << " ";
    }

    return 0;
}
```

Output:

```text
5 4 3 2 1
```

---

# 29. Example: Container With Most Water

Array:

```text
[1, 8, 6, 2, 5, 4, 8, 3, 7]
```

We have vertical lines.

We need to find two lines that can hold the maximum amount of water.

Start:

```text
[1, 8, 6, 2, 5, 4, 8, 3, 7]
 ↑                             ↑
 L                             R
```

Area formula:

```text
area = min(height[left], height[right])
       * (right - left)
```

Current:

```text
min(1, 7) * 8
= 1 * 8
= 8
```

The smaller height is:

```text
1
```

So moving `right` would not help.

We move:

```text
left++
```

This is an important Two Pointer decision:

> Move the pointer with the smaller value when trying to maximize the container area.

---

# 30. Why Does This Optimization Work?

Suppose:

```text
height[left] < height[right]
```

The area is limited by:

```text
height[left]
```

If we move `right` inward, the width becomes smaller.

But the limiting height is still `height[left]`.

So we cannot get a better area by keeping the same smaller height.

Therefore:

```text
left++
```

gives us a chance to find a taller line.

This is the type of reasoning you need to master for advanced Two Pointer problems.

---

# 31. How to Identify Two Pointer Problems?

Ask yourself:

### Question 1

Can I solve this using two positions instead of nested loops?

### Question 2

Is the array sorted?

If yes, Two Pointer should immediately come to mind.

### Question 3

Am I working from both ends?

For example:

```text
left → ← right
```

### Question 4

Am I removing duplicates or rearranging elements?

Think:

```text
slow + fast
```

### Question 5

Am I working with a linked list?

Think:

```text
slow + fast
```

### Question 6

Do I need to compare the beginning and end?

Think:

```text
left + right
```

---

# 32. Strong Signals for Two Pointer

When you see:

```text
sorted array
two elements
pair
target sum
palindrome
reverse
remove duplicates
in-place
partition
cycle
middle of linked list
```

Two Pointer should be one of your first ideas.

---

# 33. Common Mistakes

## Mistake 1: Wrong Loop Condition

For opposite pointers, usually:

```cpp
while (left < right)
```

not:

```cpp
while (left <= right)
```

unless the problem specifically needs the middle element processed.

---

## Mistake 2: Moving the Wrong Pointer

For sorted Two Sum:

```text
sum < target
    ↓
left++
```

because we need a larger value.

And:

```text
sum > target
    ↓
right--
```

because we need a smaller value.

---

## Mistake 3: Using Two Pointer Without Understanding Why

Do not just memorize:

```cpp
left++;
right--;
```

You must understand:

> **Why am I moving this pointer?**

Every pointer movement should have a reason.

---

## Mistake 4: Forgetting the Array Must Be Sorted

The classic Two Sum Two Pointer technique depends on sorted order.

For example:

```text
[1, 2, 3, 4, 6, 8]
```

works beautifully.

But:

```text
[4, 1, 8, 2, 6, 3]
```

does not give us the same information.

You may need to sort first.

But remember:

```text
sorting = O(n log n)
```

and sorting can change the original order.

---

# 34. Two Pointer After Sorting

Sometimes the original array is not sorted.

Example:

```text
[8, 1, 3, 5, 2, 7]
```

If we need a pair with a specific sum, we can sort:

```text
[1, 2, 3, 5, 7, 8]
```

Then apply Two Pointer.

But now complexity includes sorting:

```text
O(n log n)
```

The pointer scan itself is:

```text
O(n)
```

Overall:

```text
O(n log n)
```

---

# 35. Two Pointer Complexity

Most well-designed Two Pointer solutions have:

```text
Time Complexity:
O(n)
```

because each pointer moves through the data only once.

Space:

```text
O(1)
```

when no extra data structure is required.

If sorting is required:

```text
O(n log n)
```

may be the overall time complexity.

---

# 36. Two Pointer Master Templates

## Opposite Direction

```cpp
int left = 0;
int right = n - 1;

while (left < right) {

    // Calculate or compare

    if (condition) {
        left++;
    }
    else {
        right--;
    }
}
```

---

## Same Direction

```cpp
int slow = 0;

for (int fast = 0; fast < n; fast++) {

    if (condition) {

        // Process arr[fast]

        slow++;
    }
}
```

---

## Fast and Slow

```cpp
slow = head;
fast = head;

while (fast != nullptr && fast->next != nullptr) {

    slow = slow->next;
    fast = fast->next->next;
}
```

---

# 37. Two Pointer vs Nested Loops

### Brute Force

```cpp
for (int i = 0; i < n; i++) {

    for (int j = i + 1; j < n; j++) {

        // Check pair
    }
}
```

Complexity:

```text
O(n²)
```

### Two Pointer

```cpp
int left = 0;
int right = n - 1;

while (left < right) {

    // Smart pointer movement
}
```

Complexity:

```text
O(n)
```

The main improvement comes from **eliminating unnecessary comparisons**.

---

# 38. Advanced Two Pointer Problems

Once the basic pattern is clear, move toward these:

### Easy

```text
1. Reverse String
2. Valid Palindrome
3. Two Sum II
4. Remove Duplicates from Sorted Array
5. Move Zeroes
```

### Medium

```text
6. Container With Most Water
7. 3Sum
8. Sort Colors
9. Remove Element
10. Linked List Cycle
```

### Advanced

```text
11. Trapping Rain Water
12. 4Sum
13. Find the Duplicate Number
14. Middle of the Linked List
15. Minimum Window / Advanced range problems
```

---

# 39. Two Pointer Learning Roadmap

Learn in this order:

```text
LEVEL 1
│
├── Reverse Array
├── Reverse String
└── Valid Palindrome
│
LEVEL 2
│
├── Two Sum II
├── Remove Duplicates
└── Move Zeroes
│
LEVEL 3
│
├── Container With Most Water
├── 3Sum
└── Sort Colors
│
LEVEL 4
│
├── Linked List Cycle
├── Middle of Linked List
└── Find Duplicate Number
│
LEVEL 5
│
├── Trapping Rain Water
└── Advanced Two Pointer Problems
```

---

# 40. Two Pointer Cheat Sheet

```text
                 TWO POINTER
                      |
        +-------------+-------------+
        |             |             |
    Opposite       Same          Fast/Slow
    Direction     Direction
        |             |             |
    L → ← R        L → R →       Slow → 1
                                  Fast → 2
```

### Opposite Direction

```cpp
int left = 0;
int right = n - 1;

while (left < right) {
    
    // logic
    
    left++;
    right--;
}
```

### Same Direction

```cpp
int slow = 0;

for (int fast = 0; fast < n; fast++) {

    if (condition) {
        slow++;
    }
}
```

### Fast and Slow

```cpp
slow = slow->next;
fast = fast->next->next;
```

---

# 41. The Most Important Mental Model

Do not memorize only the templates.

Understand this:

> **Two Pointer means using two positions and moving them intelligently so that we do not check every possible combination.**

For example:

```text
[1, 2, 3, 4, 6, 8, 9]
 ↑                 ↑
 L                 R
```

If:

```text
arr[L] + arr[R] < target
```

move:

```text
L++
```

If:

```text
arr[L] + arr[R] > target
```

move:

```text
R--
```

If:

```text
arr[L] + arr[R] == target
```

we found the answer.

The important part is not:

```cpp
left++;
right--;
```

The important part is understanding:

> **Why should this pointer move?**

---

# 42. Final Mental Checklist

When you see a new DSA problem, ask:

```text
1. Is this an array, string, or linked list?

2. Is the array sorted?

3. Am I looking for a pair?

4. Am I comparing elements from both ends?

5. Do I need to reverse something?

6. Is this a palindrome problem?

7. Do I need to remove duplicates?

8. Do I need to modify an array in-place?

9. Can I use slow and fast pointers?

10. Can two pointers reduce O(n²) work?
```

If many answers are yes, **Two Pointer should be one of your first approaches to consider.**

---

# 43. Final Summary

Two Pointer is one of the most important techniques in DSA.

The basic idea is:

> **Use two pointers and move them intelligently instead of checking every possible combination.**

The three major patterns are:

```text
1. Opposite Direction
2. Same Direction
3. Fast and Slow
```

Remember:

```text
Opposite:
left → ← right

Same Direction:
slow → fast →

Fast / Slow:
slow → 1 step
fast → 2 steps
```

For sorted Two Sum:

```text
sum < target
    ↓
left++

sum > target
    ↓
right--

sum == target
    ↓
answer found
```

The most important lesson is:

> **Never move a pointer randomly. Every pointer movement should have a logical reason based on the problem.**

That reasoning is what turns Two Pointer from a memorized pattern into a real DSA skill.

---

# 🚀 Recommended Practice Order

```text
01. Reverse Array
02. Reverse String
03. Valid Palindrome
04. Two Sum II
05. Remove Duplicates from Sorted Array
06. Move Zeroes
07. Container With Most Water
08. 3Sum
09. Sort Colors
10. Linked List Cycle
11. Middle of Linked List
12. Find Duplicate Number
13. Trapping Rain Water
14. 4Sum
```

**Do not rush to the advanced problems. Master the pointer movement and the reason behind every movement first.**
