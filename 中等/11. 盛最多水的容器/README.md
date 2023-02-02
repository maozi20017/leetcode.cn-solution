[題目敘述](https://leetcode.cn/problems/container-with-most-water/)

```go
func maxArea(height []int) int {        
    i,j:=0,len(height)-1        //雙指針
    area:=(j-i)*min(height[i],height[j])    //面積
    for i<j{
        new_area:=(j-i)*min(height[i],height[j])
        if new_area>area{
            area=new_area
        }
        if height[i]<height[j]{     //移動高度較小的指針,因容量取決於最低的指針
            i++
        }else{
            j--
        }
    }
    return area
}
func min(x,y int)int{
    if x<y{
        return x
    }
    return y
}
