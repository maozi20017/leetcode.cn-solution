[題目敘述](https://leetcode.cn/problems/find-pivot-index/)

```go
func pivotIndex(nums []int) int {
    cnt,sum:=0,0
    for _,value :=range nums{
        sum+=value      //先計算總和
    }
    for key,value:=range nums{
        if sum-value==cnt*2{    //成為中心下標的條件就是左右的和會一樣:sum=2*cnt+value
            return key
        }
        cnt+=value
    }
    return -1
}
