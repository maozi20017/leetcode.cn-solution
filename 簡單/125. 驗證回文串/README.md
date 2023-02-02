[題目敘述](https://leetcode.cn/problems/valid-palindrome/)

```go
func isPalindrome(s string) bool {
    b := strings.Builder{}   //移除非字母數字的元素
	for _, r := range s {
		if unicode.IsLetter(r) || unicode.IsDigit(r) {  //判斷是否字母或數字
			b.WriteRune(unicode.ToLower(r)) //轉小寫並寫入b
		}
	}
	s = b.String()
    left,right:=0,len(s)-1  //前後指針
    for left < right {      
        if s[left] != s[right] {
            return false
        }
        left++
        right--
    }
    return true
}
