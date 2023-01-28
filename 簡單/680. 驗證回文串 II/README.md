[題目敘述](https://leetcode.cn/problems/valid-palindrome-ii/)  
跟[1909](https://github.com/maozi20017/leetcode.cn-solution/tree/main/%E7%B0%A1%E5%96%AE/1909.%20%E5%88%AA%E9%99%A4%E4%B8%80%E5%80%8B%E5%85%83%E7%B4%A0%E4%BD%BF%E6%95%B8%E7%B5%84%E5%9A%B4%E6%A0%BC%E9%81%9E%E5%A2%9E)很像

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
