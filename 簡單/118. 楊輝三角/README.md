[題目敘述](https://leetcode.cn/problems/pascals-triangle/)
```go
func generate(numRows int) [][]int {
    triangle := make([][]int, numRows)
    
    for i := 0; i < numRows; i++ {
        triangle[i] = make([]int, i+1)
        triangle[i][0] = 1
        
        // 計算每一行的前半部分元素
        for j := 1; j <= i/2; j++ {
            triangle[i][j] = triangle[i-1][j-1] + triangle[i-1][j]
        }
        
        // 將後半部分元素複製過來，利用對稱特性
        for j := i - 1; j >= i/2+1; j-- {
            triangle[i][j] = triangle[i][i-j]
        }
        
        triangle[i][i] = 1
    }
    
    return triangle
}
