[題目敘述](https://leetcode.cn/problems/remove-duplicates-from-sorted-array-ii/)

```go
func removeDuplicates(nums []int) int {//拿26. 刪除有序數組的重複項改的
    if len(nums) <= 2 {     
        return len(nums)
    }
    i := 2    //改變i,j 的值可適用于保留n重複項題目
    for j := 2; j < len(nums); j++ {
        if nums[j] != nums[i-2] {
            nums[i] = nums[j]
            i++
        }
    }
    return i
}
