[題目敘述](https://leetcode.cn/problems/zero-matrix-lcci/)

```go
func setZeroes(matrix [][]int)  {
    // 檢查第一行和第一列是否需要清零
    var firstRowHasZero, firstColHasZero bool       
    for i := 0; i < len(matrix[0]); i++ {
        if matrix[0][i] == 0 {
            firstRowHasZero = true
            break
        }
    }
    for i := 0; i < len(matrix); i++ {
        if matrix[i][0] == 0 {
            firstColHasZero = true
            break
        }
    }

    // 使用第一行和第一列來標記其他行和列是否需要清零
    for i := 1; i < len(matrix); i++ {
        for j := 1; j < len(matrix[0]); j++ {
            if matrix[i][j] == 0 {
                matrix[0][j] = 0
                matrix[i][0] = 0
            }
        }
    }

    // 清除其他行和列
    for i := 1; i < len(matrix); i++ {
        for j := 1; j < len(matrix[0]); j++ {
            if matrix[i][0] == 0 || matrix[0][j] == 0 {
                matrix[i][j] = 0
            }
        }
    }

    // 清除第一行和第一列
    if firstRowHasZero {
        for i := 0; i < len(matrix[0]); i++ {
            matrix[0][i] = 0
        }
    }
    if firstColHasZero {
        for i := 0; i < len(matrix); i++ {
            matrix[i][0] = 0
        }
    }
}
