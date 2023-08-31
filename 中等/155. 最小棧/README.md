[題目敘述](https://leetcode.cn/problems/min-stack/description/)
```go
type MinStack struct {
    stack []int
    minStack []int //保存當前最小值
}


func Constructor() MinStack {
    return MinStack{}
}


func (this *MinStack) Push(val int)  {
    this.stack=append(this.stack,val)

    //如果最小堆疊是空的，或者新元素小於等於最小堆疊頂部元素，則將新元素推入最小堆疊
    if len(this.minStack)==0||val<=this.minStack[len(this.minStack)-1]{
        this.minStack=append(this.minStack, val)
    }
}


func (this *MinStack) Pop()  {
    // 如果堆疊頂部元素等於最小堆疊頂部元素，則同時將其從最小堆疊中彈出
    if this.stack[len(this.stack)-1]==this.minStack[len(this.minStack)-1]{
        this.minStack=this.minStack[:len(this.minStack)-1]
    }
    this.stack=this.stack[:len(this.stack)-1]
}


func (this *MinStack) Top() int {
    return this.stack[len(this.stack)-1]
}


func (this *MinStack) GetMin() int {
    return this.minStack[len(this.minStack)-1] // 直接返回最小堆疊的頂部元素
}


/**
 * Your MinStack object will be instantiated and called as such:
 * obj := Constructor();
 * obj.Push(val);
 * obj.Pop();
 * param_3 := obj.Top();
 * param_4 := obj.GetMin();
 */
