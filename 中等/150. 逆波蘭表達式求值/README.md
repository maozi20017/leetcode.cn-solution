[題目敘述](https://leetcode.cn/problems/evaluate-reverse-polish-notation/description/)
```go
func evalRPN(tokens []string) int {
    stack:=make([]int, 0)
    for _, token:=range tokens {
        switch token {  
        case "+", "-", "*", "/"://遇到符號
            operand2:=stack[len(stack)-1]
            operand1:=stack[len(stack)-2]
            stack=stack[:len(stack)-2]
            result:=0
            switch token{
            case "+":
                result=operand1+operand2
            case "-":
                result=operand1-operand2
            case "*":
                result=operand1*operand2
            case "/":
                result=operand1/operand2
            }
            stack=append(stack, result)
        default://符號以外
            num,_:=strconv.Atoi(token)//要轉成數字
            stack=append(stack, num)
        }
    }
    return stack[0]
}
