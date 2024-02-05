[題目敘述](https://leetcode.cn/problems/binary-tree-postorder-traversal/description/)   
拿前序改的原本註解沒變
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

        ans=append(ans,node.Val)

        //堆疊為後進先出 所以要先放右節點再放左節點 這樣下次會先拿左節點   
        //記得要把左跟右相反 因為之後要倒轉
        if node.Left!=nil{
            stack=append(stack,node.Left)
        }
        if node.Right!=nil{
            stack=append(stack,node.Right)
        }
    }

    //把前序遍歷倒轉就是後序遍歷
    result := make([]int,0)
        for i := len(ans) - 1; i >= 0; i-- {
        result = append(result, ans[i])
    }
    return result
}
