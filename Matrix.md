# Matrix

## Core Functionality

Matrix, usually `m x n` (could be `n x n` in special cases), is a `2-D` representation of data, where there are `m` rows and `n` columns.

Matrix problems give inputs as an array of arrays, where the number of arrays is the number of rows, and the number of elements in each array is the same, and is the number of columns.
Hence, the first step in a matrix problem is always specifying the number of rows and number of columns:

`rows = len(matrix)`

`cols = len(matrix[0])`

## General Application
- BFS/DFS: Most common type of Matrix problem.

  `DFS` is usually used when trying to count something in the matrix, such as a group of data.
  In a `DFS` matrix problem, it's best to use recursion. Sample solution for 695:
  
  ![image](https://user-images.githubusercontent.com/54465320/201408480-8917a2c0-d2c4-407c-83b5-cc7ea7ecfea8.png)
  
  `BFS` is usually used when trying to find the shortest path from one cell to another in the matrix according to some criteria.
  In a `BFS` matrix problem. it's best to use queue. Sample solution for 1926:
  
  ![image](https://user-images.githubusercontent.com/54465320/201409732-44711f07-67e3-498e-bf06-6088b2a5e1b1.png)

- Simulation: Less common, but also common. There's usually a smart way to traverse the matrix as the problem asks, which may involve adjusting the boundaries of the traversal.
  
  Sample solution for 54:

  ![image](https://user-images.githubusercontent.com/54465320/201410403-3b542052-0eb1-4a1f-aebd-62e3c7d1dce1.png)

- Backtracking: Not common, but 79. Word Search is very important.

## Tricks
- BFS/DFS: When traversing the matrix, it is important that we note what cells have been visited by adding the cell to a hashmap `seen`.
  We could also do this by altering the value in the matrix. In a `backtracking` problem, we need to be careful to remove the cell from or not add it to `visited`,
  as we may need to visit it again (backtrack to the cell).
  
  In `BFS`, it is important that we mark visited as soon as we add it to the queue, not after we process it,
  because the cell could come after in the queue, and other cells already added to the queue could visit it again.
  
  Cleanest way to traverse is by defining all 4 directions like in sample solution for 695 above.
  We also need to be careful of the boundaries. Setting `0 <= nr < rows` makes sure that we don't traverse out of bounds.
  
- Simulation: Binary Search can be applied to sorted matrix problems.
