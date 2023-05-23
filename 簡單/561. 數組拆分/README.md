[題目敘述](https://leetcode.cn/problems/array-partition/)
```go
func arrayPairSum(nums []int) int {
    sort.Ints(nums)
    cnt:=0
    for i:=0;i<len(nums);i+=2{
        cnt+=nums[i]
    }
    return cnt
}
