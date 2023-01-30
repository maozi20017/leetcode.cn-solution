[題目敘述](https://leetcode.cn/problems/richest-customer-wealth/)

```go
//應該不用註解
func maximumWealth(accounts [][]int) int {
    max:=0
    for _,value:=range accounts{
        if sum(value)>max{
            max=sum(value)
        }
    }
    return max
}

func sum(numbers []int) int {   //加法
    total := 0
    for _,value := range numbers {
        total += value
    }
    return total
}
