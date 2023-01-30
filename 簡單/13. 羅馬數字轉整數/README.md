[題目敘述](https://leetcode.cn/problems/roman-to-integer/)

```go
func romanToInt(s string) int {
    num := map[rune]int{
        'I': 1,
        'V': 5,
        'X': 10,
        'L': 50,
        'C': 100,
        'D': 500,
        'M': 1000,
    }
    res := 0
    maxVal := 0
    for i := len(s) - 1; i >= 0; i-- {  //從右到左
        val := num[rune(s[i])]
        if val >= maxVal {  //遇到更大的加,更少的減
            res += val
            maxVal = val
        } else {    //例如題目是IV maxVal會等於V 
            res -= val
        }
    }
    return res
}
