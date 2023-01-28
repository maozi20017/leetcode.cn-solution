[題目敘述](https://leetcode.cn/problems/valid-palindrome-ii/)
跟1909很像

```go
func validPalindrome(s string) bool {
    left, right := 0, len(s)-1  //雙指針
    for left < right {
        if s[left] != s[right] {
            return isPalindrome(s, left+1, right) || isPalindrome(s, left, right-1)
        }
        left++
        right--
    }
    return true
}
func isPalindrome(s string, left, right int) bool {     
    for left < right {
        if s[left] != s[right] {
            return false
        }
        left++
        right--
    }
    return true
}
