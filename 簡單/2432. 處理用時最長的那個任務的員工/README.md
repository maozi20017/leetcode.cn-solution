[題目敘述](https://leetcode.cn/problems/the-employee-that-worked-on-the-longest-task/)

```go
func hardestWorker(n int, logs [][]int) int {   //不知道給n的意義
    ans:=[]int{logs[0][0],logs[0][1]}   //寫成陣列是為了更快
    for i:=1;i<len(logs);i++{
        if logs[i][1]-logs[i-1][1]>ans[1]{      //判斷工時比原本的長
            ans[0],ans[1]=logs[i][0],logs[i][1]-logs[i-1][1]
            continue    //或是把下面改成else if也行 沒寫會慢一點點
        }
        if logs[i][1]-logs[i-1][1]==ans[1]{ //判斷工時一樣
            ans[0]=int(math.Min(float64(logs[i][0]),float64(ans[0])))   //取小的
        }
    }
    return ans[0]
}
