[題目敘述](https://leetcode.cn/problems/open-the-lock/description/)   

```go
func openLock(deadends []string, target string) int {
    //創建死亡數字哈希表
    deadendset:=map[string]bool{}
    for _,value:=range deadends{
        deadendset[value]=true
    }

    if deadendset["0000"]==true{
        return -1
    }else if target=="0000"{
        return 0
    }

    //初始化隊列和已訪問狀態
    queue:=[]string{"0000"}
    visited:=map[string]bool{"0000":true}
    step:=0

    //BFS
    for len(queue)>0{
        size:=len(queue)
        for i:=0;i<size;i++{
            code:=queue[i]
            neighbors:=generateNeighbors(code)
            for _,neighbor:=range neighbors{
                //跟目標相同
                if neighbor==target{
                    return step+1//因為是neighbor step要+1
                }

                //不在死亡數字上和沒訪問過
                if deadendset[neighbor]==false&&visited[neighbor]==false{
                    queue=append(queue,neighbor)
                    visited[neighbor]=true
                }
            }
        }
        queue=queue[size:]
        step++
    }
    return -1
}

//生成鄰居
func generateNeighbors(code string)[]string{
    neighbors:=[]string{}
    for i:=0;i<len(code);i++{
        digit:=int(code[i]-'0')
        for _,value:=range []int{1,-1}{
            newdigit:=(digit+value+10)%10//防止負數和超過9的
            neighbor:=code[:i]+strconv.Itoa(newdigit)+code[i+1:]
            neighbors=append(neighbors,neighbor)
        }
    }
    return neighbors
}
