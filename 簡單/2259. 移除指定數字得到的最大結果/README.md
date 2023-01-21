[題目敘述](https://leetcode.cn/problems/remove-digit-from-number-to-maximize-result/)

```go
func removeDigit(number string, digit byte)string{
    var max string
    for key,value:=range number{        //遍歷
        if value==rune(digit){      //類型不同要轉換
            s := number[:key] + number[key+1:]  //移除
            if s>max{
                max=s
            }
        }
    }
    return max
}
