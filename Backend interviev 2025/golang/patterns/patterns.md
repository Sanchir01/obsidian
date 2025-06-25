#### Generator

```go

func generate(dataprops[]int) <-chan int{
	mychan := make(chan int)
	go func(){
		defer close(mychan)
		for _, v := range dataprops{
			mychan <- v
		}
	}()
	return mychan
}
func main() {
	data := []int{1, 2, 3, 4, 5}
	ch := generate(data)

	for val := range ch {
		fmt.Println(val)
	}
}
```