[題目敘述](https://leetcode.cn/problems/ransom-note/)

```go
func canConstruct(ransomNote string, magazine string) bool {
    mp:=make(map[rune]int)      //建表 沒了
    for _,value:=range magazine{
        mp[value]++
    }
    for _,value:=range ransomNote{
        mp[value]--
        if mp[value]<0{
            return false
        }
    }
    return true
}
