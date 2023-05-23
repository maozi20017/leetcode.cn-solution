[題目敘述](https://leetcode.cn/problems/reverse-string/)

```go
func reverseString(s []byte)  {
    //就這?
    i,j:=0,len(s)-1
    for !(i>j){
        if s[i]!=s[j]{
            s[i],s[j]=s[j],s[i]
        }
        i++
        j--
    }
}
