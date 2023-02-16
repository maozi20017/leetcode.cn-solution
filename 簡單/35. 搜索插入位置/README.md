[題目敘述](https://leetcode.cn/problems/search-insert-position/)

```go
func searchInsert(nums []int, target int) int {
    left, right := 0, len(nums)-1       //二分法
    for left <= right {
        mid := left + (right-left)/2
        if nums[mid] == target {
            return mid
        } else if nums[mid] < target {
            left = mid + 1
        } else {
            right = mid - 1
        }
    }
    return left
}
