# code



## for loop print 1,2,3 and use orhter goroutine


```go
package main

import (
	"fmt"
	"sync"
)

func main() {
	const rounds = 10

	ch := make(chan int)

	chG1 := make(chan struct{} )
	chG2 := make(chan struct{} )
	chG3 := make(chan struct{})

	var wg sync.WaitGroup
	wg.Add(1)

	// 输入goroutine
	
	
	//g1
	go func() {
		
		for  range chG1 { 
			fmt.Println("g1:? ") 
			if  val ,ok:= <-ch ; ok{
				fmt.Println("g1: ",val) 
				chG2 <- struct{}{} // 触发g3开始执行
				wg.Done()
			}
		}
	}()
	//g2
	go func() { 
		for  range chG2 { 
			if  val ,ok:= <-ch ; ok{
				fmt.Println("g2: ",val) 
				chG3 <- struct{}{} // 触发g2开始执行
				wg.Done()
			}
		}
	}()
		//g3
		go func() { 
			for  range chG3 { 
				if  val ,ok:= <-ch ; ok{
					fmt.Println("g3: ",val) 
					chG1 <- struct{}{} // 触发g3开始执行
					wg.Done()
				}
			}
		}() 

		
		go func() {
			
			chG1 <- struct{}{} // 触发g1开始执行
			
			for i := 0; i < rounds; i++ {
				wg.Add(3)
				ch <- 1  
				ch <- 2 
				ch <- 3 
		
			}
			wg.Done()
			
		}()

	wg.Wait()
	close(ch)
	close(chG1)
	close(chG2)
	close(chG3)
}

```

want to control more model type

```go
package main

import (
	"fmt"
	"sync"
)

func main() {
	const rounds = 10

	ch := make(chan int)

	chG1 := make(chan struct{})
	chG2 := make(chan struct{})
	chG3 := make(chan struct{})
	var mutex sync.Mutex

	var wg sync.WaitGroup
	wg.Add(3)

	// 输入goroutine
	
	

	func
	//g1
	go func() {
		defer wg.Done()
		for  range chG1 { 
			if  val ,ok:= <-ch ; ok{
				fmt.Println("g1: ",val) 
				mutex.Unlock()
			}
		}
	}()
	//g2
	go func() {
		defer wg.Done()
		for  range chG2 { 
			if  val ,ok:= <-ch ; ok{
				fmt.Println("g2: ",val) 
				mutex.Unlock()
			}
		}
	}()
		//g3
		go func() {
			defer wg.Done()
			for  range chG3 { 
				if  val ,ok:= <-ch ; ok{
					fmt.Println("g3: ",val) 
					mutex.Unlock()
				}
			}
		}() 


		go func() {
			fmt.Println("g1:?！ ") 
			mutex.Lock()
			chG1 <- struct{}{} // 触发g1开始执行
			
			for i := 0; i < rounds; i++ {
				
				ch <- 1 
				mutex.Lock()
				chG2 <- struct{}{} // 触发g2开始执行
				ch <- 2
				mutex.Lock()
				chG3 <- struct{}{} // 触发g3开始执行
				
				ch <- 3
				mutex.Lock()
				chG1 <- struct{}{} // 触发g1开始执行
		
			}
			mutex.Unlock()
			close(ch)
			close(chG1)
			close(chG2)
			close(chG3)
		}()

	wg.Wait()
}
```

let me use array to control?

```go

package main

import (
	"fmt"
	"sync"
)

func main() {
	const rounds = 10
	//go rountine number
	const GRN = 4
	ch := make(chan int, 1)
	chArr := make([]chan struct{}, GRN)
	var mutex sync.Mutex
	var wg sync.WaitGroup
	wg.Add(GRN)

	// 输入goroutine

	var loopCustomer = func(index int, ch chan int, chG chan struct{}, mutex *sync.Mutex, wg *sync.WaitGroup) {
		defer wg.Done()
		for range chG {
			if val, ok := <-ch; ok {
				fmt.Println(string(index+1)+": ", val)
				mutex.Unlock()
			}

		}

	}
	for i := 0; i < GRN; i++ {
		chArr[i] = make(chan struct{})
		go loopCustomer(i, ch, chArr[i], &mutex, &wg)
	}

	go func() {

		for i := 0; i < rounds; i++ {
			for i := 0; i < GRN; i++ {
				mutex.Lock()
				ch <- (i + 1)
				chArr[i] <- struct{}{}
			}
		}
		close(ch)
		for i := 0; i < GRN; i++ {
			close(chArr[i])
		}

	}()

	wg.Wait()
}

```