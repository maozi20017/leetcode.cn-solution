[題目敘述](https://leetcode.cn/problems/max-consecutive-ones/)

```go
func findMaxConsecutiveOnes(nums []int) int {
    //兩種寫法
    cnt,max:=0,0
    for _,value :=range nums{
        if value==1{
            cnt++
        }else{
            if max<cnt{
                max=cnt
            }
            cnt=0            
        }
    }
    if max<cnt{
        max=cnt
    }
    //快慢指針
    // slow,fast,max:=-1,0,0
    // for key,value:=range nums{
    //     if value==1{
    //         if slow==-1{
    //             slow,fast=key,key
    //         }else{
    //             fast++
    //         }
    //         if max<fast-slow+1{
    //             max=fast-slow+1
    //         }
    //     }else if slow!=-1{
    //         slow=-1
    //     }
    // }
    // return max
}
