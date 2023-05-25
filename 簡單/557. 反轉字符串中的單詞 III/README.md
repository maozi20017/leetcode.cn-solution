[題目敘述](https://leetcode.cn/problems/reverse-words-in-a-string-iii/)


```go
func reverseWords(s string) string {
    //快慢指針
    runes := []rune(s)
    slow, fast := 0, 0
    for key, value := range runes {
        if value == ' ' {
            for fast = key - 1; fast > slow; fast-- {
                runes[slow], runes[fast] = runes[fast], runes[slow]
                slow++
            }
            slow = key + 1
        }
    }
    
    // 最後一個詞會交換不到要多寫一個迴圈
    for fast = len(runes) - 1; fast > slow; fast-- {
        runes[slow], runes[fast] = runes[fast], runes[slow]
        slow++
    }
    
    return string(runes)
}
