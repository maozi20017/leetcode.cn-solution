[題目敘述](https://leetcode.cn/problems/implement-stack-using-queues/description/)
```go
type MyStack struct {
    inqueue, outqueue []int
}

// Constructor 用來初始化 MyStack 物件，返回一個空的 MyStack。
func Constructor() MyStack {
    return MyStack{}
}

// Push 函式將一個元素 x 壓入堆疊中。
func (this *MyStack) Push(x int) {
    // 將元素 x 壓入 outqueue
    this.outqueue = append(this.outqueue, x)
    
    // 將 inqueue 的元素一個一個移動到 outqueue，以保證最新壓入的元素在堆疊的頂部
    for len(this.inqueue) > 0 {
        this.outqueue = append(this.outqueue, this.inqueue[0])
        this.inqueue = this.inqueue[1:]
    }
    
    // 將 outqueue 與 inqueue 交換，以維護堆疊的狀態
    this.inqueue, this.outqueue = this.outqueue, this.inqueue
}

// Pop 函式移除堆疊頂部的元素並返回它。
func (this *MyStack) Pop() int {
    ans := this.inqueue[0]
    this.inqueue = this.inqueue[1:]
    return ans
}

// Top 函式返回堆疊頂部的元素，但不移除它。
func (this *MyStack) Top() int {
    return this.inqueue[0]
}

// Empty 函式檢查堆疊是否為空。
func (this *MyStack) Empty() bool {
    return len(this.inqueue) == 0
}

/**
 * 使用示例:
 * obj := Constructor();
 * obj.Push(x);
 * param_2 := obj.Pop();
 * param_3 := obj.Top();
 * param_4 := obj.Empty();
 */
