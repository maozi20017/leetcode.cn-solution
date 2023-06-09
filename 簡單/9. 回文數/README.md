[題目敘述](https://leetcode.cn/problems/palindrome-number/)
```go 
func isPalindrome(x int) bool {
    if x<0 || (x != 0 && x%10 == 0) {// 如果 x 是負數或者是以 0 结尾的正整數，返回 false
        return false
    }
    y := 0// 保存反轉後的數字

    for x > y { // 只處理原始數字的一半
        y = y*10 + x%10
        x /= 10
    }
    return x == y || x == y/10  //左邊判斷x為偶數位數 右邊判斷x為奇數位數
}
