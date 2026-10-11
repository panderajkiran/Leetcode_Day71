# Leetcode_Day71
# Day 71: Matrix Block Sum

**LeetCode Problem:** 1314. Matrix Block Sum  
**Difficulty:** Medium  
**Topic:** Matrix, Arrays, Prefix Sum  
**Language:** Java

## Problem Statement

Given an `m × n` matrix and an integer `k`, return a matrix where each element `answer[i][j]` is the sum of all elements within a block extending up to `k` cells in every direction from position `(i, j)`.

The block must stay within the boundaries of the original matrix.

## Approach: Brute Force

I solved this problem using nested loops to calculate the sum of each block.

1. Find the number of rows `m` and columns `n`.
2. Create a new matrix called `answer` to store the results.
3. Visit every cell `(i, j)` in the original matrix.
4. Calculate the valid row boundaries using `Math.max(0, i - k)` and `Math.min(m - 1, i + k)`.
5. Calculate the valid column boundaries using `Math.max(0, j - k)` and `Math.min(n - 1, j + k)`.
6. Add all elements within those boundaries and store the sum in `answer[i][j]`.
7. Return the resulting matrix.

Using `Math.max()` and `Math.min()` prevents accessing cells outside the matrix.

## Java Solution

```java
class Solution {
    public int[][] matrixBlockSum(int[][] mat, int k) {
        int m = mat.length;
        int n = mat[0].length;

        int[][] answer = new int[m][n];

        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                int sum = 0;

                for (int r = Math.max(0, i - k);
                     r <= Math.min(m - 1, i + k); r++) {

                    for (int c = Math.max(0, j - k);
                         c <= Math.min(n - 1, j + k); c++) {
                        sum += mat[r][c];
                    }
                }

                answer[i][j] = sum;
            }
        }

        return answer;
    }
}
```

## Example

**Input:**
```text
mat = [[1,2,3],
       [4,5,6],
       [7,8,9]]
k = 1
```

**Output:**
```text
[[12,21,16],
 [27,45,33],
 [24,39,28]]
```

**Explanation:**

For the center element `(1,1)`, the block contains all nine elements. Their sum is `45`.

For corner and edge elements, only the cells within the matrix boundaries are included.

## Complexity Analysis

Let `m` be the number of rows, `n` be the number of columns, and `k` be the block radius.

- **Time Complexity:** O(m × n × min(m, 2k + 1) × min(n, 2k + 1))
- **Space Complexity:** O(m × n) for the answer matrix, excluding the output.

## What I Learned

- How to traverse a two-dimensional matrix using nested loops.
- How to calculate the boundaries of a block around a cell.
- How `Math.max()` and `Math.min()` help prevent index errors.
- How to break a matrix problem into smaller calculations.

## Takeaway

Today's problem reminded me that a big task becomes easier when we solve it one small section at a time.

Just like calculating each block in a matrix, progress comes from paying attention to the small steps that build the final result.

**Day 71 complete — another problem solved, another lesson learned.**
