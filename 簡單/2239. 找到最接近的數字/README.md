[題目敘述](https://leetcode.cn/problems/find-closest-number-to-zero/)

```go
func findClosestNumber(nums []int) int {
    var min_range =nums[0]                                      //初始化為第一個數字
    for i:=1; i<len(nums) ;i++{                                 //遍歷
        test1:=math.Abs(float64(nums[i]))                       //絕對值
        test2:=math.Abs(float64(min_range))                     //絕對值
        if test1<test2||(test1==test2 && nums[i]> min_range){   //要交換只有兩種情況:1.絕對值過後新的比原本的小   2.相同且數字比原本的大
            min_range=nums[i]                                   
        }
    }
    return min_rang
}
