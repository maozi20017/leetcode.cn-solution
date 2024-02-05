[題目敘述](https://leetcode.cn/problems/binary-tree-postorder-traversal/description/)   
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func postorderTraversal(root *TreeNode) []int {
    //建立數組
    ans:=make([]int,0)
    
    //二叉樹為空回傳空數組
    if root==nil{
        return ans
    }

    //建立堆疊
    stack:=[]*TreeNode{root}

    //前序遍歷
    for len(stack)>0{
        //當前節點
        node:=stack[len(stack)-1]

        //把節點從堆疊移出
        stack=stack[:len(stack)-1]

        //將節點值插入到數組的最前面
        ans=append([]int{node.Val},ans...)

        //堆疊為後進先出 所以要先放左節點再放右節點 這樣下次會先拿右節點
        //因為現在插入數組的方式是從最前面
        if node.Left!=nil{
            stack=append(stack,node.Left)
        }
        if node.Right!=nil{
            stack=append(stack,node.Right)
        }
    }

    return ans
}
