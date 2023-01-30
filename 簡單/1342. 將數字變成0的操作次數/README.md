[題目敘述](https://leetcode.cn/problems/number-of-steps-to-reduce-a-number-to-zero/)

```go
//可以用位運算但這樣寫比較直觀
func numberOfSteps(num int) int { 
    cnt:=0
    for num!=0{
        if num%2==0{    //偶數
            num/=2
        }else{      //奇數
            num--
        }
        cnt++
    }
    return cnt
}
