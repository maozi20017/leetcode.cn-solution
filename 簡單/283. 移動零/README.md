[題目敘述](https://leetcode.cn/problems/move-zeroes/)

```go
func moveZeroes(nums []int){
    i := 0
    for key,value:=range nums {
        if value != 0 {     //不為0
            nums[i],nums[key] = nums[key],nums[i]   //交換
            i++ //指針向前
        }
    }
    return 
}
