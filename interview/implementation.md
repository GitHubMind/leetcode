# Implementation

## Question 1:  When init will start in process?

    In the begin when you start main.go

    if you have it in orther package like A, and A include C package

    initlializtion  process will follow sequence : C init() -> A init()-> main init() 

    is  import -> var /const -> init() -> main function

    var should be focus , because of it will run fristly.

    for example:
    ```
    var b = func() int {
            log.Println("TEST")
    }

    func main(){
        log.Println("test2")
    }
    // Test
    // Test2
    ```

## Allocate on stack or heap?
   
   In System.Ecah  function has its own stack,then  if value  can't ecesape the scope of fucntion .It will be set in stack, whether if will be heap.

```go

func foo() *int {
	v := 11
	return &v
}

func main() {
	m := foo()
	println(*m) // 11
}
```

    summary：
    Te heap can be used by orhter functions,including the main function.


## Can you compare two interface ?

    Yes,but ont thing need to care about that  already  initizlized  struct can't compare.

```go

  type Stu struct {
	Name string
}

type StuInt interface{}

func main() {
	var stu1, stu2 StuInt = &Stu{"Tom"}, &Stu{"Tom"}
	var stu3, stu4 StuInt = Stu{"Tom"}, Stu{"Tom"}
	var stu5, stu6 StuInt = Stu{"Tom"}, Stu{"Tom2"}
	fmt.Println(stu1 == stu2) // false
	fmt.Println(stu3 == stu4) // true
	fmt.Println(stu5 == stu6) // false
}


```


## can go compare  two nil ？

```go
    var p *int = nil
	var i interface{} = p
	fmt.Println(i == p) // true
	fmt.Println(p == nil) // true
	fmt.Println(i == nil) // false

```

##  can you tell about Garbage Collection  process ?

    + stw
    + scan all mmonory , mark Object to black node  in stack   
    + Blacl -> Grep -> white ，delete 
    +  mark Termination, need STW
  

 
##  how you can check  about the memory allocator
```go

func main(){
        var ms runtime.MemStats
        printMemStat(ms)

        //----------------------------------  
        // you can write any code here
        //----------------------------------
        intArr := make([]int, 900000)
        for i := 0; i < len(intArr); i++ {
            intArr[i] = rand.Int()
        }
        //------------------------------------
        time.Sleep(5 * time.Second)

        printMemStat(ms)

}
func printMemStat(ms runtime.MemStats) {
        runtime.ReadMemStats(&ms)
        fmt.Println("--------------------------------------")
        fmt.Println("Memory Statistics Reporting time: ", time.Now())
        fmt.Println("--------------------------------------")
        fmt.Println("Bytes of allocated heap objects: ", ms.Alloc)
        fmt.Println("Total bytes of Heap object: ", ms.TotalAlloc)
        fmt.Println("Bytes of memory obtained from OS: ", ms.Sys)
        fmt.Println("Count of heap objects: ", ms.Mallocs)
        fmt.Println("Count of heap objects freed: ", ms.Frees)
        fmt.Println("Count of live heap objects", ms.Mallocs-ms.Frees)
        fmt.Println("Number of completed GC cycles: ", ms.NumGC)
        fmt.Println("--------------------------------------")
}
```