[題目敘述](https://leetcode.cn/problems/minimum-cost-of-buying-candies-with-discount/)

[sort.Sort(sort.Reverse(sort.IntSlice(cost)))](https://blog.csdn.net/qq_43279457/article/details/121730095)
```go
func minimumCost(cost []int) int {
    total_cost:=0
    sort.Sort(sort.Reverse(sort.IntSlice(cost))) //上方超連結
    for i:=0;i<len(cost);i++{
        if (i+1)%3!=0{
            total_cost+=cost[i]
        }
    }
    return total_cost
}
