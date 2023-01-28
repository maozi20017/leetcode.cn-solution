[題目敘述](https://leetcode.cn/problems/number-of-common-factors/)

```go
func commonFactors(a int, b int) int {
    //找兩數的最大公因數的因數
    ans:=0
    g := gcd(a, b)
	for i := 1; i*i <= g; i++ { //循環到根號g就可以找到所有因數
		if g%i == 0 {
			ans++
			if i*i < g {
				ans++
			}
		}
	}
	return ans
    /* 簡單版本直接枚舉
    ans:=0
    for i:=1;i<=int(math.Min(float64(a),float64(b)));i++{
        if a%i==0&&b%i==0{
            ans++
        }
    }
    return ans
    */
}

func gcd(a, b int) int {    //輾轉相除法
	for a != 0 {
		a, b = b%a, a
	}
	return b
}
