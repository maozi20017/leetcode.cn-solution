[題目敘述](https://leetcode.cn/problems/reformat-date/)

```go
func reformatDate(date string) string {
    r := strings.NewReplacer("st ", " ", "nd ", " ", "rd ", " ", "th ", " ")        //把字串處理成能用的
	data := r.Replace(date)   
	theTime,_ := time.Parse("2 Jan 2006", data)       //換成時間值
    return theTime.Format("2006-01-02")     //更換格式
}
