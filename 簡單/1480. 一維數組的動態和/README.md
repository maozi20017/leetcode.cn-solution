[題目敘述](https://leetcode.cn/problems/running-sum-of-1d-array/)

```go
func runningSum(nums []int) []int {   //應該不用註解ㄅ
    for i:=1;i<len(nums);i++{
        nums[i]+=nums[i-1]
    }
    return nums
}
