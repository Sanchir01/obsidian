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

#### Fan in

```go

func fanin(ctx context.Context, chans[]int) <-chan int{
	mychan := make(chan int)
	go func(){
		wg := &sync.WaitGroup{}
		for _, ch := range chans{
			wg.Add(1)
			go func (){
				defer wg.Done()
				for {
					select {
						case v, ok := <-ch:
							if !ok{
								return
							}
							select {
								case out <- v:
								case <-ctx.Done():
									return
							}
						case <-ctx.Done():	
							return
					}
					
				}
			}()
		}
		wg.Wait()
		close(mychan)
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

Fan out

```go

func fanout(
ctx context.Context, in chan int, numChans int, f func(int) int
) []chan int{
	mychan := make(chan int,numChans)
	for i := range numChans {
		chans[i] = pipeline(in,f)
	}
	return mychan
}

func pipeline(ctx context.Context, in chan int, f func(int) int) chan int {
	out := chan(chan int)
	go func(){
		for v := range in {
			out <- f(v)
		}
	}()
	return out
}
func main() {
	data := []int{1, 2, 3, 4, 5}
	ch := generate(data)

	for val := range ch {
		fmt.Println(val)
	}
}
```