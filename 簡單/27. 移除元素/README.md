[題目敘述](https://leetcode.cn/problems/remove-element/)

```go
func removeElement(nums []int, val int) int {   //拿移動零那題來改的
    i := 0
    for key,value:=range nums {
        if value != val {     //不等於val
            nums[i],nums[key] = nums[key],nums[i]   //交換
            i++ //指針向前
        }
    }
    return i        //i同時也意味著不等於val的個數
}
