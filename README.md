### go-timewheel

自用魔改时间轮。

#### usage

```go
package main_test

func TestTimeWheelAdd(t *testing.T) {
	tw, err := NewTimeWheel(1*time.Second, 3)
	if err != nil {
		fmt.Println(err)
	}
	tw.Start()
	defer tw.Stop()
	var wg sync.WaitGroup
	wg.Add(1)
	tw.Add(0*time.Second, func() {
		defer wg.Done()
		log.Println("hello world")
	})
	wg.Wait()
}

```