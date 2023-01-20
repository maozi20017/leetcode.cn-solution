[題目敘述](https://leetcode.cn/problems/add-to-array-form-of-integer/)

```go
func addToArrayForm(num []int, k int) (ans []int) {
    for i := len(num) - 1; i >= 0; i-- {    //運算
        sum := num[i] + k%10
        k /= 10
        if sum >= 10 {
            k++
            sum -= 10
        }
        ans = append(ans, sum)
    }
    for ; k > 0; k /= 10 {      //k的位數比num多的位數
        ans = append(ans, k%10)
    }
    reverse(ans)    //倒轉
    return ans
}

func reverse(num []int) {
    for i, n := 0, len(num); i < n/2; i++ {
        num[i], num[n-1-i] = num[n-1-i], num[i]
    }
}
