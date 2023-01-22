[題目敘述](https://leetcode.cn/problems/jBjn9C/)

```go
type KthLargest struct {
    sort.IntSlice       //小到大排序
    k int
}

func Constructor(k int, nums []int) KthLargest {
    kl := KthLargest{k: k}      //初始化堆 這裡就排序了
    for _, val := range nums {  //塞入堆中
        kl.Add(val)
    }
    return kl
}

func (kl *KthLargest) Push(v interface{}) {     //推
    kl.IntSlice = append(kl.IntSlice, v.(int))
}

func (kl *KthLargest) Pop() interface{} {   
    a := kl.IntSlice
    v := a[len(a)-1]
    kl.IntSlice = a[:len(a)-1]
    return v
}

func (kl *KthLargest) Add(val int) int {
    heap.Push(kl, val)
    if kl.Len() > kl.k {        //如超出長度
        heap.Pop(kl)
    }
    return kl.IntSlice[0]       //回到一開始
}

/**
 * Your KthLargest object will be instantiated and called as such:
 * obj := Constructor(k, nums);
 * param_1 := obj.Add(val);
 */
