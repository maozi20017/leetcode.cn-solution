[題目敘述](https://leetcode.cn/problems/minimum-recolors-to-get-k-consecutive-black-blocks/)

```go
func minimumRecolors(blocks string, k int) int {        //滑動窗口問題
    minw:=strings.Count(blocks,"W")                     //用strings.count找一段字串中有多少匹配到的字符
    for i:=0;i<len(blocks)-k+1;i++{                     
        if minw>strings.Count(blocks[i:i+k],"W"){
            minw=strings.Count(blocks[i:i+k],"W")
        }
    }

    return minw
}
