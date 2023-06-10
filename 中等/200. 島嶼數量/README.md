[題目敘述](https://leetcode.cn/problems/number-of-islands/)  
特別用了指標優化
```go
func numIslands(grid [][]byte) int {
    // 檢查網格是否為空
    if len(grid) == 0 || len(grid[0]) == 0 {
        return 0
    }

    rows, cols := len(grid), len(grid[0])

    count := 0 // 島嶼計數器
    for i := 0; i < rows; i++ {
        for j := 0; j < cols; j++ {
            if grid[i][j] == '1'{
                dfs(&grid, i, j) // 呼叫 DFS 函數進行島嶼探索
                count++ // 每次探索完一個島嶼，計數器增加
            }
        }
    }

    return count // 返回島嶼的總數量
}

func dfs(grid *[][]byte, row, col int) {
    // 如果當前座標越界    或是    探索到水或是已經探索過的陸地 則返回
    if row < 0 || row >= len(*grid) || col < 0 || col >= len((*grid)[0]) || (*grid)[row][col] != '1' {
        return
    }

    (*grid)[row][col] = '2' // 將當前座標標記為已訪問

    // 遞迴探索上、下、左、右四個方向
    dfs(grid, row-1, col) // 上
    dfs(grid, row+1, col) // 下
    dfs(grid, row, col-1) // 左
    dfs(grid, row, col+1) // 右
}

