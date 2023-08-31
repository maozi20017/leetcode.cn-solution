[題目敘述](https://leetcode.cn/problems/perfect-squares/description/)   
```go
//動態規劃
func numSquares(n int) int {
    dp := make([]int, n+1)
    for i:=1;i<=n;i++{
        dp[i]=i //最壞情況是全由1組成
        for j:=1; j*j <= i; j++ {//拆成多個小問題 先算前面的數字的最少次數
            dp[i]=min(dp[i],dp[i-j*j]+1)  
        }
    }
    return dp[n]
}

func min(a, b int)int{
    if a<b{
        return a
    }
    return b
}
