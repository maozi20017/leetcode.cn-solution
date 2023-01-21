[題目敘述](https://leetcode.cn/problems/da-yin-cong-1dao-zui-da-de-nwei-shu-lcof/)

```go
func printNumbers(n int) []int {
    res := make([]string, int(math.Pow10(n)-1))
	count := 0
	var dfs func([]byte, int, int)
	dfs = func(num []byte, idx, max int) { 
		if idx == max {
			res[count] = string(num)    //num遞迴完成放入res
			count++
			return
		}
		for i := '0'; i <= '9'; i++ {
			num[idx] = byte(i)
			dfs(num, idx+1, max)
		}
	}
	for i := 1; i <= n; i++ {
		num := make([]byte, i)
		for b := '1'; b <= '9'; b++ {   //最前面第一位必定為1-9 後面幾位則進入dfs
			num[0] = byte(b)    
			dfs(num, 1, i)
		}
	}
	return res
/*餵chatgpt的解釋
如果n=2，外層循環將遍歷兩次。

第一次，i的值為1，內層循環創建了一個長度為1的新字節切片 "num"。它從1開始遍歷所有從1到9的數字，將每個數字添加到 "num"字節切片中。對於每個數字，它調用dfs函數，使用 "num" 字節切片，從第一個索引開始，並將1作為排列組合的最大長度。

第二次，i的值為2，內層循環創建了一個長度為2的新字節切片 "num"。它從1開始遍歷所有從1到9的數字，將每個數字添加到 "num"字節切片的第一個索引。對於每個數字，它調用dfs函數，使用 "num" 字節切片，從第二個索引開始，並將2作為排列組合的最大長度。

在dfs函數中，它會遍歷從'0'到'9'的所有數字，並將它們添加到由"num"字節切片表示的當前排列組合中，在當前索引。如果當前索引等於最大長度(2)，則將當前排列組合添加到"res"切片中，並將計數變量增加1。


    這題應該是要考大數但這樣也能過
    s:= make([]int, 0)
    for i:=1;i<int(math.Pow(10,float64(n)));i++{
        s=append(s,i)    
    }
    return s
    */
}
