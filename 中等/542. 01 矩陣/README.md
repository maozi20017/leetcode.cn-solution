[題目敘述](https://leetcode.cn/problems/01-matrix/description/)
```go
func updateMatrix(mat [][]int) [][]int {
    // 獲取矩陣的行和列
    row, col := len(mat), len(mat[0])

    // 使用隊列，將矩陣中的 0 的位置加入隊列，並將非 0 的位置設為-1
    queue := make([][2]int, 0)
    for i := 0; i < row; i++ {
        for j := 0; j < col; j++ {
            if mat[i][j] == 0 {
                queue = append(queue, [2]int{i, j})
                mat[i][j] = 0
            } else {
                mat[i][j] = -1
            }
        }
    }

    // 定義四個方向：右、下、左、上
    dir := [][]int{{0, 1}, {1, 0}, {0, -1}, {-1, 0}}

    // 使用 BFS（廣度優先搜尋）來更新矩陣中每個位置到最近的 0 的距離
    for len(queue) > 0 {
        // 取出隊列中的第一個元素
        cell := queue[0]
        queue = queue[1:]

        // 遍歷四個方向
        for i := 0; i < len(dir); i++ {
            // 新的位置
            newX, newY := cell[0]+dir[i][0], cell[1]+dir[i][1]

            // 邊界檢查以及更新到最近的 0 的距離
            if newX >= 0 && newY >= 0 && newX < row && newY < col && mat[newX][newY] == -1 {
                mat[newX][newY] = mat[cell[0]][cell[1]] + 1
                queue = append(queue, [2]int{newX, newY})
            }
        }
    }

    return mat
}
