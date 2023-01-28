[題目敘述](https://leetcode.cn/problems/reverse-only-letters/)

```go
func reverseOnlyLetters(s string) string {
    ans := []byte(s)    //因string是不可變的要額外宣告
    left,right:=0,len(s)-1  //雙指針
    for {
        for left < right && !unicode.IsLetter(rune(s[left])) { // 左邊沒偵測到字母
            left++
        }
        for right > left && !unicode.IsLetter(rune(s[right])) { // 右邊沒偵測到字母
            right--
        }
        if left >= right {
            break
        }
        ans[left], ans[right] = ans[right], ans[left]
        left++
        right--
    }
    return string(ans)
}
