[題目敘述](https://leetcode.cn/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/)  這題真的很難
```go
func buildTree(inorder []int, postorder []int) *TreeNode {
    size := len(inorder)
    if size == 0 {
        return nil
    }

    //位置
    postIndex, inIndex := len(postorder)-1, len(inorder)-1

    // 根節點會是後序遍歷的最後一個
    root := &TreeNode{Val: postorder[size-1]}

    postIndex--

    // 建立堆疊
    stack := []*TreeNode{root}

    // 遍歷
    for postIndex >= 0 {
        // 每次循環都會變回nil
        var currNode *TreeNode

        // 回溯，直到堆疊頂部元素不等於中序數組指針指向的值
        // 用於找父節點，最後輸出完成時將是當前子樹的父節點
        for len(stack) > 0 && stack[len(stack)-1].Val == inorder[inIndex] {
            currNode = stack[len(stack)-1]
            stack = stack[:len(stack)-1] // 彈出堆疊頂部元素
            inIndex--                   // 向左移動到下一個中序遍歷的元素
        }

        if currNode != nil { // 如果不為空，代表當前處理的節點有左子節點
            currNode.Left = &TreeNode{Val: postorder[postIndex]} // 將左子節點添加到當前節點的左子樹上
            stack = append(stack, currNode.Left) // 將左子節點加入堆疊，等待後續處理其子樹
            postIndex--                         // 移動到下一個後序遍歷的元素
        } else { // 如果是空的，代表當前處理的節點沒有左子節點，則是右子節點
            currNode = &TreeNode{Val: postorder[postIndex]} // 創建一個右子節點
            stack[len(stack)-1].Right = currNode // 將右子節點連接到其父節點的右子樹上
            stack = append(stack, currNode)     // 將右子節點加入堆疊，等待後續處理其子樹
            postIndex--                         // 移動到下一個後序遍歷的元素
        }
    }
    return root
}
