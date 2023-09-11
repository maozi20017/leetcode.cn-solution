[題目敘述](https://leetcode.cn/problems/flood-fill/description/)
```go
func floodFill(image [][]int, sr int, sc int, color int) [][]int {
    if image[sr][sc] == color {
        return image // 如果起始點的顏色已經是目標顏色，無需填充，直接返回原圖像
    }
    oldColor := image[sr][sc] // 儲存起始點的舊顏色
    queue := [][]int{{sr, sc}} // 創建一個佇列，用於實現廣度優先搜索

    directions := [][]int{{1, 0}, {-1, 0}, {0, 1}, {0, -1}} // 上、下、左、右四個方向的偏移量

    for len(queue) > 0 { // 當佇列不為空時執行洪水填充
        start := queue[0] // 取出佇列的第一個元素
        queue = queue[1:] // 移除佇列的第一個元素
        r, c := start[0], start[1] // 取得行和列的坐標

        image[r][c] = color // 將當前像素的顏色設置為目標顏色

        for _, value := range directions { // 對四個方向進行遍歷
            newR, newC := r+value[0], c+value[1] // 計算新的行和列坐標
            if newR >= 0 && newR < len(image) && newC >= 0 && newC < len(image[0]) && image[newR][newC] == oldColor {
                // 如果新坐標在圖像範圍內且與舊顏色相同，則將其添加到佇列中，以便進一步處理
                queue = append(queue, []int{newR, newC})
            }
        }
    }

    return image // 返回填充後的圖像
}
