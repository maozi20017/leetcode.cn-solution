[題目敘述](https://leetcode.cn/problems/daily-temperatures/description/)
```go
func dailyTemperatures(temperatures []int) []int {
    n := len(temperatures) // 溫度陣列的長度
    ans := make([]int, n)   // 創建一個用來存放結果的陣列
    stack := []int{}        // 使用堆疊來記錄索引，儲存溫度遞減的索引

    for i := 0; i < n; i++ {
        for len(stack) > 0 && temperatures[i] > temperatures[stack[len(stack)-1]] {
            prevIndex := stack[len(stack)-1] // 堆疊頂部索引對應的前一個溫度的索引
            stack = stack[:len(stack)-1]     // 彈出堆疊頂部元素
            ans[prevIndex] = i - prevIndex   // 計算溫度升高所需的天數差，並存入結果陣列
        }
        stack = append(stack, i) // 將當前索引壓入堆疊中，維護溫度遞減的堆疊
    }

    return ans
}
