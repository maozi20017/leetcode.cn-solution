[題目敘述](https://leetcode.cn/problems/last-stone-weight/)  
  
```go
func lastStoneWeight(stones []int) int {
    sort.Sort(sort.Reverse(sort.IntSlice(stones)))  //排序
    for len(stones)>=2{
        if stones[0]-stones[1]!=0{    //不同時才要增加元素
            stones=append(stones,stones[0]-stones[1])
        }
        stones=stones[2:]   //刪掉比較的元素
        sort.Sort(sort.Reverse(sort.IntSlice(stones)))
    }
    if len(stones)>0{   //有就回傳
        return stones[0]
    }
    return 0
}
