[題目敘述](https://leetcode.cn/problems/reverse-vowels-of-a-string/)  
byte 處理 ASCII 字符更高效，因為它們的大小僅為 1 字節。  
然而，如果需要處理非 ASCII 字符，則必須使用 rune，因為它們的大小為 4 字節。
```go
func reverseVowels(s string) string {
    vowels := "aeiouAEIOU"
    i,j:=0,len(s)-1
    slice:=[]byte(s)    
    for i < j {
        for i < j && !strings.ContainsRune(vowels, rune(slice[i])) {    //驗證當前rune是否是母音(存在在vowels當中)
            i++
        }
        for i < j && !strings.ContainsRune(vowels, rune(slice[j])) {
            j--
        }
        slice[i], slice[j] = slice[j], slice[i]
        i++
        j--
    }
    return string(slice)
}
