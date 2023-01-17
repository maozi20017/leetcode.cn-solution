[題目敘述](https://leetcode.cn/problems/dKk3P7/)

```go
func isAnagram(s string, t string) bool {
    if s==t||len(s)!=len(t){    //一樣或長度不同就不是變位詞
        return false
    }

    cnt := map[rune]int{}       //建map
    for _, ch := range s {      //計算出現與次數
        cnt[ch]++
    }
    for _, ch := range t {      //出現過的扣掉
        cnt[ch]--
        if cnt[ch] < 0 {        
            return false
        }
    }
    return true
}
