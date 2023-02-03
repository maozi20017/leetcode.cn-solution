[題目敘述](https://leetcode.cn/problems/minimum-size-subarray-sum/)

```go
func minSubArrayLen(target int, nums []int) int {
    n := len(nums)
    if n == 0 {
        return 0
    }
    left, right, sum := 0, 0, 0     //雙指針 總和
    minLen := n + 1     //最短長度
    for right < n {
        sum += nums[right]
        right++
        for sum >= target {
            minLen = min(minLen, right-left)
            sum -= nums[left]
            left++
        }
    }
    if minLen == n+1 {      //如果依舊等於n+1代表不存在符合條件的子數組
        return 0
    }
    return minLen
}

func min(x, y int) int {
    if x < y {
        return x
    }
    return y
}
