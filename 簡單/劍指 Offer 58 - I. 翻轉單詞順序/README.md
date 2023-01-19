[題目敘述](https://leetcode.cn/problems/fan-zhuan-dan-ci-shun-xu-lcof/)

```go
func reverseWords(s string) string {
    var res string
    var i = len(s) - 1
    var j = i
    for i >= 0 {        //從最右邊開始
        for i >= 0 && s[i] == ' '{
            i--
        }
        j = i       //紀錄並繼續往左
        for i >= 0 && s[i] != ' '{
            i--
        }
        res = res + s[i+1:j+1] + " "    //把單字提取出來   
    }
    return strings.TrimRight(res, " ")  //因為每個都加了最後後面會多一個所以要消除右邊空白
}
