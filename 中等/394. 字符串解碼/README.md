[題目敘述](https://leetcode.cn/problems/decode-string/description/)  
其實可以用單個stack儲存數字和字串，但會太亂就一樣用2個  
```go
func decodeString(s string) string {
    stack, numstack := []string{}, []int{}
    ans := ""
    num := 0
    for _, value := range s {
        if unicode.IsDigit(value) { // 如果是數字字符
            num = num*10 + int(value-'0') // 將字符轉換為數字並更新數字變數
        } else if value == '[' { // 如果是左括號
            numstack = append(numstack, num) // 壓入數字堆疊
            stack = append(stack, ans) // 壓入答案堆疊
            ans = "" // 重置答案字串
            num = 0 // 重置數字變數
        } else if value == ']' { // 如果是右括號
            re := numstack[len(numstack)-1] // 取出最上層的數字
            numstack = numstack[:len(numstack)-1] // 移除最上層的數字
            prestr := stack[len(stack)-1] // 取出最上層的答案
            stack = stack[:len(stack)-1] // 移除最上層的答案
            ans = prestr + strings.Repeat(ans, re) // 將答案重複 re 次並加到 prestr 後面
        } else {
            ans += string(value) // 如果是字母字符，直接加到答案字串後面
        }
    }
    return ans
}
