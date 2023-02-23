[題目敘述](https://leetcode.cn/problems/longest-common-prefix/)
  
分治
```go
func longestCommonPrefix(strs []string) string {
    if len(strs) == 1 {
        return strs[0]
    }
    mid := len(strs) / 2
    leftPrefix := longestCommonPrefix(strs[:mid])
    rightPrefix := longestCommonPrefix(strs[mid:])
    return commonPrefix(leftPrefix, rightPrefix)
    
}

func commonPrefix(str1, str2 string) string {
    minLen := min(len(str1), len(str2))
    for i := 0; i < minLen; i++ {
        if str1[i] != str2[i] {
            return str1[:i]
        }
    }
    return str1[:minLen]
}

func min (x,y int)int{
    if x<y{
        return x
    }
    return y
}  
```  
縱向  
```go
func longestCommonPrefix(strs []string) string {
    if len(strs) == 1 {
        return strs[0]
    }
    minLen := len(strs[0])
    for i := 1; i < len(strs); i++ {
        minLen=min(minLen,len(strs[i]))
    }
    for i := 0; i < minLen; i++ {
        prefix := strs[0][:i+1]
        for j := 1; j < len(strs); j++ {
            if !strings.HasPrefix(strs[j], prefix) {
                return strs[0][:i]
            }
        }
    }
    return strs[0][:minLen]
}
func min (x,y int)int{
    if x<y{
        return x
    }
    return y
}
```  
橫向  
```go
func longestCommonPrefix(strs []string) string {
    if len(strs) == 1 {
        return strs[0]
    }
    prefix := strs[0]
    for _, s := range strs {
        for !strings.HasPrefix(s, prefix) {
            prefix = prefix[:len(prefix)-1]
            if prefix == "" {
                return ""
            }
        }
    }
    return prefix
}
func min (x,y int)int{
    if x<y{
        return x
    }
    return y
}
