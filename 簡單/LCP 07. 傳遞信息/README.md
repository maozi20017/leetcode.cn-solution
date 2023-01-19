[題目敘述](https://leetcode.cn/problems/chuan-di-xin-xi/)

```go
func numWays(n int, relation [][]int, k int) int {    //動態規劃
    dp := make([]int, n)
    dp[0] = 1
    for i := 0; i < k; i++ {
        next := make([]int, n)
        for _, r := range relation {
            src, dst := r[0], r[1]    //建議把每次循環的結果記下來
            next[dst] += dp[src]
        }
        dp = next
    }
    return dp[n-1]    //最後產生的dp等於每個節點經過的次數
}
