[題目敘述](https://leetcode.cn/problems/implement-queue-using-stacks/description/)
```go
type MyQueue struct {
    inStack,outStack []int
}


func Constructor() MyQueue {
    return MyQueue{}
}


func (this *MyQueue) Push(x int)  {
    this.inStack=append(this.inStack,x)
}

func (this *MyQueue) in2out() {
    for len(this.inStack)>0 {
        this.outStack=append(this.outStack,this.inStack[len(this.inStack)-1])
        this.inStack=this.inStack[:len(this.inStack)-1]
    }
}

func (this *MyQueue) Pop() int {
    if len(this.outStack)==0 {
        this.in2out()
    }
    x:=this.outStack[len(this.outStack)-1]
    this.outStack=this.outStack[:len(this.outStack)-1]
    return x
}


func (this *MyQueue) Peek() int {
    if len(this.outStack) == 0 {
        this.in2out()
    }
    return this.outStack[len(this.outStack)-1]
}


func (this *MyQueue) Empty() bool {
    return len(this.inStack)==0&&len(this.outStack)==0
}


/**
 * Your MyQueue object will be instantiated and called as such:
 * obj := Constructor();
 * obj.Push(x);
 * param_2 := obj.Pop();
 * param_3 := obj.Peek();
 * param_4 := obj.Empty();
 */
