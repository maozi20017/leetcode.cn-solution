[題目敘述](https://leetcode.cn/problems/diagonal-traverse/)

```go
func findDiagonalOrder(mat [][]int) []int {
    m, n := len(mat), len(mat[0])
    ans := make([]int, 0, m*n)
    for k := 0; k < m+n-1; k++ {        //k=i+j
        if k%2 == 0 {       //偶數
            i := min(k, m-1)        //起始點
            j := k - i
            for i >= 0 && j < n {       //遍歷
                ans = append(ans, mat[i][j])
                i--
                j++
            }
        } else {        //奇數
            j := min(k, n-1)        //起始點
            i := k - j
            for i < m && j >= 0 {       //遍歷
                ans = append(ans, mat[i][j])
                i++
                j--
            }
        }
    }
    return ans
}

func min(a, b int) int {
    if a < b {
        return a
    }
    return b
}
