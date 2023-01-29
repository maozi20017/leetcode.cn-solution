[題目敘述](https://leetcode.cn/problems/count-the-digits-that-divide-a-number/)

```go
func countDigits(num int) int {
    //應該不用註解ㄅ
    cnt,n:=0,num    
    for n!=0{
        if num%(n%10)==0{
            cnt++
        }
        n=n/10
    }
    return cnt
}
