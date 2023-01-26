[題目敘述](https://leetcode.cn/problems/detect-pattern-of-length-m-repeated-k-or-more-times/)

```go
func containsPattern(arr []int, m int, k int) bool {
    n := len(arr)
    for l := 0; l < n - m * k + 1; l++ {
        offset := 0
        for offset < m * k {
            if arr[l + offset] != arr[l + offset % m] { //arr[l + offset]目前的 arr[l + offset % m]原本的
                break
            }
            offset += 1
        }
        if offset >= m * k {    //至少
            return true
        }
    }
    return false
}
