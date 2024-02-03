[題目敘述](https://leetcode.cn/problems/keys-and-rooms/description/)
```go
func canVisitAllRooms(rooms [][]int) bool {
    // 取得房間的總數
    length := len(rooms)

    // 用一個布林切片表示每個房間是否被訪問過，初始都為 false
    visited := make([]bool, length)

    // 從第一個房間開始，將其標記為已訪問
    visited[0] = true

    // 使用堆疊來實現深度優先搜索
    stack := []int{0}

    // 開始 DFS 遍歷
    for len(stack) > 0 {
        // 取出堆疊的頂部元素，表示當前所在的房間
        room := stack[len(stack)-1]
        stack = stack[:len(stack)-1]

        // 遍歷當前房間的鑰匙，如果相連的房間未被訪問過，標記為已訪問並加入堆疊
        for i:=0;i<len(rooms[room]);i++ {
            if visited[rooms[room][i]]==false {
                visited[rooms[room][i]] = true
                stack = append(stack, rooms[room][i])
            }
        }
    }

    // 檢查是否所有房間都被訪問過，如果有未訪問過的房間，返回 false
    for i := 0; i < length; i++ {
        if visited[i]==false {
            return false
        }
    }

    // 所有房間都被訪問過，返回 true
    return true
}
