[題目敘述](https://leetcode.cn/problems/uncommon-words-from-two-sentences/)

```go
func uncommonFromSentences(s1 string, s2 string) []string {
    sm1,sm2:=make(map[string]int),make(map[string]int)
    field1,field2:=strings.Fields(s1),strings.Fields(s2)    //按照空白分割
    //建map
    mp(sm1,field1)  
    mp(sm2,field2)  
    ans:=[]string{}
    //互相比較
    compareMap(sm1,sm2,&ans)    
    compareMap(sm2,sm1,&ans)
    return ans
}

func mp(sm map[string]int,field []string){
    for _,value :=range field{
        sm[value]++
    }
    return
}

//需要使用指針不然值無法傳遞回去 如沒使用值只會在函式內更新
func compareMap(mp1, mp2 map[string]int, ans *[]string){  
    for key, value := range mp1 {
        if value == 1 && mp2[key] == 0 {
            *ans = append(*ans, key)
        }
    }
    return 
}
