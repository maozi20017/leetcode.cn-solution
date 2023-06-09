[題目敘述](https://leetcode.cn/problems/design-circular-queue/)
```go
type MyCircularQueue struct {
	capacity int   // 佇列的容量
	queue    []int // 儲存元素的切片
}

// Constructor 初始化 MyCircularQueue 並設定容量
func Constructor(k int) MyCircularQueue {
	return MyCircularQueue{capacity: k}
}

// EnQueue 將元素加入佇列尾部，若佇列已滿則回傳 false
func (this *MyCircularQueue) EnQueue(value int) bool {
	if this.IsFull() {
		return false
	}
	this.queue = append(this.queue, value)
	return true
}

// DeQueue 刪除佇列頭部的元素，若佇列為空則回傳 false
func (this *MyCircularQueue) DeQueue() bool {
	if this.IsEmpty() {
		return false
	}
	this.queue = this.queue[1:len(this.queue)]
	return true
}

// Front 取得佇列頭部的元素，若佇列為空則回傳 -1
func (this *MyCircularQueue) Front() int {
	if this.IsEmpty() {
		return -1
	}
	return this.queue[0]
}

// Rear 取得佇列尾部的元素，若佇列為空則回傳 -1
func (this *MyCircularQueue) Rear() int {
	if this.IsEmpty() {
		return -1
	}
	return this.queue[len(this.queue)-1]
}

// IsEmpty 檢查佇列是否為空，是則回傳 true，否則回傳 false
func (this *MyCircularQueue) IsEmpty() bool {
	return len(this.queue) == 0
}

// IsFull 檢查佇列是否已滿，是則回傳 true，否則回傳 false
func (this *MyCircularQueue) IsFull() bool {
	return len(this.queue) == this.capacity
}



/**
 * Your MyCircularQueue object will be instantiated and called as such:
 * obj := Constructor(k);
 * param_1 := obj.EnQueue(value);
 * param_2 := obj.DeQueue();
 * param_3 := obj.Front();
 * param_4 := obj.Rear();
 * param_5 := obj.IsEmpty();
 * param_6 := obj.IsFull();
 */
