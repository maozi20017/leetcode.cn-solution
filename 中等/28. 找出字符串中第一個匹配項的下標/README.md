[題目敘述](https://leetcode.cn/problems/find-the-index-of-the-first-occurrence-in-a-string/)  
  
```go
func strStr(haystack string, needle string) int {
    return strings.Index(haystack, needle)
    //想搞KMP但搞不出來
    // next:=make([]int,len(needle))
    // next[0]=-1
    // for i,j:=0,1;j<len(needle);j++{
    //     if needle[i]==needle[j]&&j+1<len(needle){
    //         next[j+1]=i+1
    //         i++
    //     }else{
    //         if i!=0{
    //             i = next[i]
    //         }
    //     }
    // }
    // for h_key,n_key:=0,0;n_key<len(needle)&&h_key<len(haystack);{
    //     if haystack[h_key]!=needle[n_key]{
    //         if n_key==0{
    //             h_key++
    //         }else{
    //             n_key=next[n_key]
    //         }
    //         continue
    //     }
    //     h_key++
    //     n_key++
    //     if n_key==len(needle){
    //         return h_key-len(needle)
    //     }
    // }
    // return -1
}
