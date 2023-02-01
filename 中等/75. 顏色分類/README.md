[題目敘述](https://leetcode.cn/problems/sort-colors/)

```go
func sortColors(nums []int)  {  //題目規定不能用內建的sort函數
    p0, p2 := 0, len(nums) - 1
    for i := 0; i <= p2; i++ {
        if nums[i] == 0 {   //0排前面
            nums[i], nums[p0] = nums[p0], nums[i]
            p0++
        } else if nums[i] == 2 {    //2排後面
            nums[i], nums[p2] = nums[p2], nums[i]
            p2--
            i--
        }
    }
    return 
}
