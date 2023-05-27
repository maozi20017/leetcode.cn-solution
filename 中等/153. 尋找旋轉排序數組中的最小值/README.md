[題目敘述](https://leetcode.cn/problems/find-minimum-in-rotated-sorted-array/)

```go
func findMin(nums []int) int {
    //二分查找
    left,right:=0,len(nums)-1
    for left<right{
        mid:=(left+right)/2
        if nums[mid] > nums[right] {
            left = mid + 1
        } else {
            right = mid
        }
    }
    return nums[left]
}
