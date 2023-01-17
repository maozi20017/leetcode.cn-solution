[題目敘述](https://leetcode.cn/problems/longer-contiguous-segments-of-ones-than-zeros/)

```go
func checkZeroOnes(s string) bool {
    cnt,cnt0max,cnt1max:=1,0,0
    for i:=1;i<len(s);i++{    //遍歷
        if s[i]!=s[i-1]{      //只有在目前的跟前一個不同時才要計算其他一律遞增
            if s[i]=='0'&&cnt>cnt1max{  //目前是0之前是1的連續
                cnt1max=cnt
            }
            if s[i]=='1'&&cnt>cnt0max{  //目前是1之前是0的連續
                cnt0max=cnt
            }
            cnt=1
        }else{
            cnt++
        }
    }
    
    if s[len(s)-1] == '0' && cnt > cnt0max {    //遍歷完後沒有計算最後的會出錯 例如111000這種的
        cnt0max = cnt
    }
    if s[len(s)-1] == '1' && cnt > cnt1max {
        cnt1max = cnt
    }

    return cnt1max>cnt0max
}
