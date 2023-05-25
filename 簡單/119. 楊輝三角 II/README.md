[題目敘述](https://leetcode.cn/problems/pascals-triangle-ii/)

```go
func getRow(rowIndex int) []int {
    result := make([]int, rowIndex+1)
    result[0] = 1

    for i := 1; i <= rowIndex; i++ {
        // 利用公式計算每個元素的值
        result[i] = result[i-1] * (rowIndex - i + 1) / i
    }

    return result
}
