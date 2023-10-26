
### Here is the assignment asnwer

```python

from typing import List


def max_moves(grid: List[List[int]]) -> int:
    m = len(grid)
    n = len(grid[0])
    
    dp = [[0] * n for _ in range(m)]
    
    # right to left
    for j in range(n-2, -1, -1):
        for i in range(m):
            # calculate the max number of moves for each cell
            if i > 0 and grid[i][j] < grid[i-1][j+1]:
                dp[i][j] = max(dp[i][j], dp[i-1][j+1] + 1)
            if grid[i][j] < grid[i][j+1]:
                dp[i][j] = max(dp[i][j], dp[i][j+1] + 1)
            if i < m-1 and grid[i][j] < grid[i+1][j+1]:
                dp[i][j] = max(dp[i][j], dp[i+1][j+1] + 1)
    
    # find the max number of moves in the last column
    max_moves = max(dp[i][0] for i in range(m))
    
    return max_moves



# tests

tests = [
    {
        "input" : [[2, 4, 3, 5], [5, 4, 9, 3], [3, 4, 2, 11], [10, 9, 13, 15]],
        "output" : 3
    },
    {
        "input" : [[3, 2, 4], [2, 1, 9], [1, 1, 7]],
        "output" : 0
    }
]


for test in tests:
    if max_moves(test['input']) == test['output']:
        print("Passed")
    else:
        print(test['input'], "failed")

```
