[題目敘述](https://leetcode.cn/problems/merge-intervals/)

```go
func merge(intervals [][]int) [][]int {
    sort.Slice(intervals, func(i, j int) bool { return intervals[i][0] < intervals[j][0] })     //起始點小到大排序

    merged := [][]int{intervals[0]}
    for i := 1; i < len(intervals); i++ {
        interval:=intervals[i]
        if interval[0] <= merged[len(merged)-1][1] {        //融合
            merged[len(merged)-1][1] = max(merged[len(merged)-1][1], interval[1])
        } else {        //沒融合就加入
            merged = append(merged, interval)
        }
    }
    return merged
}

func max(x,y int)int{
    if x<y{
        return y
    }
    return x
}
