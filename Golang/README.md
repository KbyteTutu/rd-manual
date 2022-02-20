# Golang

### 初始化空变量
map: `var a map[string]string`  
slice: `var b = make([]string, 0)`

### 初始化赋值变量
map: `tmpMap := map[int]string{0 : "a", 1 : "b"}`  
slice: `slis := []int{1,2,3,4,5,6,7,8}`  
数组：`nums := [...]int{1,2,3,4,5,6,7,8}`
 
### 遍历
数组
```go
for k, v:= range nums{
    // k 为下标，v 为对应的值
    fmt.Println(k, v, " ")
}
```
slice
```go
for k, v:= range slis{
    // k 为下标，v 为对应的值
    fmt.Println(k, v, " ")
}
```
map
```go
for k, v:= range tmpMap{
    // k 为键值，v 为对应值
    fmt.Println(k, v, " ")
}
```
模拟while循环
```go
for i < l {
	if i == l - 1 {
		break
	} else {
		i += 1
	}
}
```
