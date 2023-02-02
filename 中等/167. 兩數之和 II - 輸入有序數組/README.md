[題目敘述](https://leetcode.cn/problems/two-sum-ii-input-array-is-sorted/)

```go
func twoSum(numbers []int, target int) []int {
    i,j:=0,len(numbers)-1   //雙指針對撞
    for i!=j{
        ans:= numbers[i]+numbers[j]
        if ans==target{     //一樣回傳index
            return []int{i+1,j+1}
        }else if ans<target{    //小於目標數左指針右移
            i++
        }else if ans>target{    //大於目標數右指針左移
            j--
        }
    }
    return []int{}
}
