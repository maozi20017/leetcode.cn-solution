[題目敘述](https://leetcode.cn/problems/divide-array-into-equal-pairs/)

```go
func divideArray(nums []int) bool {
    mp:=make(map[int]int)   //建立map
    for _,value:= range nums{   //成對會恢復成0
        if mp[value]==0{
            mp[value]++
        }else{
            mp[value]--
        }
    }
    for _,value:=range mp{
        if value!=0{    //不為0=不是相等數對
            return false
        }
    }
    return true
}
