[題目敘述](https://leetcode.cn/problems/remove-duplicates-from-sorted-array/)

```go
func removeDuplicates(nums []int) int {
    i := 0  //慢指針
    for j := 1; j < len(nums); j++ {    //快指針
        if nums[j] != nums[i] {     //如果找到跟i不同的元素複製到i+1的位置
            i++
            nums[i] = nums[j]
        }
    }
    return i + 1
}
