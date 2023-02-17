[題目敘述](https://leetcode.cn/problems/rotate-image/)

```go
func rotate(matrix [][]int)  {
    n:=len(matrix)
    // 水平
    for i:=0;i<n/2;i++{
        matrix[i],matrix[n-1-i]=matrix[n-1-i],matrix[i]
    }
    // 對角線
    for i:=0;i<n;i++{
        for j:=0;j<i;j++{
            matrix[i][j],matrix[j][i]=matrix[j][i],matrix[i][j]
        }
    }
}
