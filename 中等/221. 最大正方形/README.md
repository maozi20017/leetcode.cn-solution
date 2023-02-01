[題目敘述](https://leetcode.cn/problems/maximal-square/)

```go
func maximalSquare(matrix [][]byte) int {
    //dp表示以(i,j)為右下角且只包含1的正方形的邊長最大值
    //為何dp長度是m+1:避免越界錯誤,例如,當要判斷的正方形在最左上,裡面的值需要靠左上,左,上來判斷,這也是為甚麼dp會從i和j從1開始判斷
    m, n := len(matrix), len(matrix[0])
    dp := make([][]int, m+1)       
    for i := range dp {     
        dp[i] = make([]int, n+1)
    }
    maxLen := 0
    for i := 1; i <= m; i++ {
        for j := 1; j <= n; j++ {
            if matrix[i-1][j-1] == '1' {
                dp[i][j] = min(dp[i-1][j-1], min(dp[i-1][j], dp[i][j-1])) + 1
                maxLen = max(maxLen, dp[i][j])
            }
        }
    }
    return maxLen * maxLen
}
//僅是比大小,go沒有內建給int類型的max,min函數
func min(x, y int) int {
    if x < y {
        return x
    }
    return y
}

func max(x, y int) int {
    if x > y {
        return x
    }
    return y
}
