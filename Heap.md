# Heap

## Core Functionality

Heap can be a max heap or a min heap. Heap is a tree-based structure where the parent node is greater/smaller than or equal to its children nodes.

Heap can be used as a sorting tool, and usually represented as a list rather than a tree.
It is faster than the best sorting algorithm (Timsort), which can be achieved at `O(nlogn)` worst, `O(nlogn)` average,
and `O(n)` best, with `O(n)` space, where `n` is the size of the heap.

Heap is faster in sorting because it doesn't sort from smallest to fastest like a regular sorting algorithm, but makes the array a tree with the heap property.
Sorting with a heap in Python uses `heapq.heapify`, which **builds** a heap in `O(n)`.

Popping from a heap will take the highest node of the tree, which is the smallest/largest element depending on if it's a min/max heap.
Popping and pushing to heap will maintain the heap property.
Popping takes `O(logn)`. In Python, pop with `heapq.heappop(heap)`, push to heap with `heapq.heappush(heap, value)`.
Both take `O(logn)`.

## General Application
- Problems where we need to find the *k(-th) largest/smallest/most-frequent/closest* elements in an array since we can pop and process the smaller/larger elements.

- Problems where we need to *prioritize some elements over others* based on their frequencies. These include 621, 767, 1405, 1338.
We would also need to pair heap with a `Counter` to keep track of the frequencies for this sort of problems.

- Problems where we need to *take an element, process (and possibly change) it, and possibly put it back to the array.*
If we need to change it and put it back, we may need to maintain the desired order, and heap works best and fastest

## Sample Code
Solution for 1405:

![image](https://user-images.githubusercontent.com/54465320/200936849-df2dda45-8e92-4391-ae7d-27f3788ee774.png)

## Tricks

- In the second type of problems, similar to the sample code, we can keep a variable `prev` to indicate the last letter used and its updated frequency, 
so that we don't use it just yet. After using another letter, we push it back and free `prev`.

- Keep a `hashmap` to record when an element was updated in certain problems.
