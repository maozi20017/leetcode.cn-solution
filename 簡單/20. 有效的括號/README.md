[題目敘述](https://leetcode.cn/problems/valid-parentheses/description/)
```go
func isValid(s string) bool {
    stack := []rune{} // 初始化一個 rune 型切片作為堆疊
    mapping := map[rune]rune{ // 映射右括號到對應的左括號
        ')': '(',
        ']': '[',
        '}': '{',
    }

    for _, char := range s { // 遍歷輸入字串中的每個字符
        if char == '(' || char == '[' || char == '{' {
            stack = append(stack, char) // 將左括號壓入堆疊
        } else if char == ')' || char == ']' || char == '}' {
            if len(stack) == 0 || stack[len(stack)-1] != mapping[char] {
                return false // 如果堆疊是空的或對應不正確，則括號無效
            }
            stack = stack[:len(stack)-1] // 從堆疊中彈出一個左括號
        }
    }

    return len(stack) == 0 // 如果堆疊最終為空，則括號有效
}
