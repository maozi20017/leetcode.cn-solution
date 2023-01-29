[題目敘述](https://leetcode.cn/problems/remove-outermost-parentheses/)

```go
func removeOuterParentheses(s string) string {
    var ans[]rune  
    cnt:=0//st用來確認是否在最外層的括號
    for _, c := range s {
        if c == ')' {   //找到就回到上個括號
            cnt--
        }
        if cnt > 0 {    //如果是最外圈的st會等於0
            ans = append(ans, c)
        }
        if c == '(' {   //進入括號
            cnt++
        }
    }
    return string(ans)
}
