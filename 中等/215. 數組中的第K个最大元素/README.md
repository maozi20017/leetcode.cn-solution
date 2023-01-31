[題目敘述](https://leetcode.cn/problems/kth-largest-element-in-an-array/)

```go
func findKthLargest(nums []int, k int) int {    
    sort.Ints(nums) //排序 這個比較快
    return nums[len(nums)-k]
    /*
    sort.Sort(sort.Reverse(sort.IntSlice(nums)))    //倒序
    return nums[k-1]
    */
}
