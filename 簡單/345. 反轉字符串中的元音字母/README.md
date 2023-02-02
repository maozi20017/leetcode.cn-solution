[題目敘述](https://leetcode.cn/problems/reverse-vowels-of-a-string/)

```go
func reverseVowels(s string) string {
    vowels := "aeiouAEIOU"
    i,j:=0,len(s)-1
    slice:=[]rune(s)
    for i < j {
        for i < j && !strings.ContainsRune(vowels, slice[i]) {    //驗證當前rune是否是母音(存在在vowels當中)
            i++
        }
        for i < j && !strings.ContainsRune(vowels, slice[j]) {
            j--
        }
        slice[i], slice[j] = slice[j], slice[i]
        i++
        j--
    }
    return string(slice)
}
