[題目敘述](https://leetcode.cn/problems/missing-number/)  
兩種寫法(第一種比較快)  
```go
func missingNumber(nums []int) int {
    //用全部總和-nums總和判斷
    n:=len(nums)
    expected:=n*(n+1)/2
    actual:=0
    for _, num := range nums {
        actual+=num
    }
    return expected-actual
}

或是

func missingNumber(nums []int) int {
    //建表
    t:=make([]int,len(nums)+1)
    for _,value:=range nums{    //例如如果有0 則t[0]=1
        t[value]=1
    }
    for key,value:=range t{ //遍歷
        if value==0{
            return key
        }
    }
    return -1
}
