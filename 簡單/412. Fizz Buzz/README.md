[題目敘述](https://leetcode.cn/problems/fizz-buzz/)

```go
func fizzBuzz(n int) []string {
    ans:=make([]string,0)
    for i:=1;i<=n;i++{
        if i%15==0{
            ans=append(ans,"FizzBuzz")
        }else if i%3==0{
            ans=append(ans,"Fizz")
        }else if i%5==0{
            ans=append(ans,"Buzz")
        }else{
            ans=append(ans,strconv.Itoa(i))
        }
    }
    return ans
    /*官方用&strings.Builder{}指針 效率差不多
    ans:=make([]string,0)
    for i := 1; i <= n; i++ {
        sb := &strings.Builder{}
        if i%3 == 0 {
            sb.WriteString("Fizz")
        }
        if i%5 == 0 {
            sb.WriteString("Buzz")
        }
        if sb.Len() == 0 {
            sb.WriteString(strconv.Itoa(i))
        }
        ans = append(ans, sb.String())
    }
    return ans
    */
}
