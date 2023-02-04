[題目敘述](https://leetcode.cn/problems/design-linked-list/)

```go
type MyLinkedList struct {
    head *ListNode
    size int
}

func Constructor() MyLinkedList {
    return MyLinkedList{&ListNode{}, 0}
}

func (this *MyLinkedList) Get(index int) int {
    if index < 0 || index >= this.size {        //檢查索引是否小於0或大於等於鏈表的大小，是則返回-1
        return -1
    }
    cur := this.head
    for i := 0; i <= index; i++ {
        cur = cur.Next
    }
    return cur.Val
}

func (this *MyLinkedList) AddAtHead(val int) {
    this.AddAtIndex(0, val)
}

func (this *MyLinkedList) AddAtTail(val int) {
    this.AddAtIndex(this.size, val)
}

func (this *MyLinkedList) AddAtIndex(index, val int) {
    if index > this.size {      //如果插入的索引位置大於鏈表大小，則不進行操作並返回
        return
    }
    index = max(index, 0)       //如果插入的索引位置小於0，則修正為0。
    this.size++
    pred := this.head
    for i := 0; i < index; i++ {        //移動到插入位置的前面一個位置
        pred = pred.Next
    }
    toAdd := &ListNode{val, pred.Next}      //其Next屬性指向pred的下一個ListNode
    pred.Next = toAdd       //將pred的Next屬性指向toAdd
}

func (this *MyLinkedList) DeleteAtIndex(index int) {
    if index < 0 || index >= this.size {        //檢查索引是否小於0或大於鏈表的大小，是則退出
        return
    }
    this.size--
    pred := this.head
    for i := 0; i < index; i++ {        //移動到索引的前一個位置
        pred = pred.Next
    }
    pred.Next = pred.Next.Next
}

func max(a, b int) int {
    if b > a {
        return b
    }
    return a
}

/**
 * Your MyLinkedList object will be instantiated and called as such:
 * obj := Constructor();
 * param_1 := obj.Get(index);
 * obj.AddAtHead(val);
 * obj.AddAtTail(val);
 * obj.AddAtIndex(index,val);
 * obj.DeleteAtIndex(index);
 */
