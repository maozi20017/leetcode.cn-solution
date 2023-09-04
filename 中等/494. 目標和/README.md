[題目敘述](https://leetcode.cn/problems/target-sum/)
```go
func findTargetSumWays(nums []int, target int) (count int) {
    // 初始化一個二維陣列dp，dp[i][j]表示前i個數構成和為j的表達式的數量
    // 使用dp陣列進行動態規劃
    // dp[i][j] = dp[i-1][j-nums[i]] + dp[i-1][j+nums[i]]
    
    n := len(nums)
    // 假設sum(nums)是所有數字的和，因為表達式可以是正數或負數，所以最小值是-sum(nums)，最大值是sum(nums)
    sum := 0
    for _, num := range nums {
        sum += num
    }
    if target < -sum || target > sum {
        return 0 // 目標值不在可能的範圍內，無法構造
    }

    // 創建dp陣列並初始化
    dp := make([][]int, n)
    for i := 0; i < n; i++ {
        dp[i] = make([]int, 2*sum+1)
    }
    
    // 處理第一個數字的情況
    dp[0][nums[0]+sum] += 1
    dp[0][-nums[0]+sum] += 1

    // 動態規劃主體
    for i := 1; i < n; i++ {
        for j := -sum; j <= sum; j++ {
            if dp[i-1][j+sum] > 0 {
                dp[i][j+sum+nums[i]] += dp[i-1][j+sum]
                dp[i][j+sum-nums[i]] += dp[i-1][j+sum]
            }
        }
    }

    return dp[n-1][target+sum]
}
