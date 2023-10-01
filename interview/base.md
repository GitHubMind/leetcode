# Base question

## Question 1: The different between `:=` and  `=` ?

**A:**  

    var xx string     =1 

    const text string =1 

    xx :=""              

    so  
         := //declare and assign
         =  //assign

---

## Q2: what is pointer

**A** : lt's simple and base question, a pointer is a variable that stores a monery address.

such as :

         var a int 
         var b *int
         log.Prinlnt(b) // nil
         b:=a
         a=100
         log.println(b) // 0x0023asda
         log.Println(*b) // 100

## Q3 what is goroutine

    这个有点难用英文表达,goroutine

    1.这个就是是轻量用户进程，他调度的时候不涉及内核态的变化,上下文切换的时候开销低于传统的线程和进程
    2.在goalng表现就是 GO FUNCTION去新起一个,MAIN本身就是Goroutine,不过是一个默认开始执行的线程。
    3.goroutine 本身大小最大只有2k,相对于进程来说开销极小并且达到高并发的水准
## Q4 How to concatenate string  high efficiently [x]
 
   1 Concatenate it in memory  so that  string array can't expansion and only read .-> it will new one memory address
   ```
        var str string.builder
        str.writeString("test")    
   ```
## Q5 what is rune type

    Rune is an int32 type, and it's particulary usefor for dealing with Unicode,Chinese characters.
 
```GO
    s := "GO编程"
	log.Println(len(s)) //8
	runeS := []rune(s)
	log.Println(len(runeS)) //4

```
## Q6 How can you check if the content of two string slice is equal ?

    two type :

    ```GO
        // simple and good
        func equaltest(a,b []string) bool {
          for i, v := range a {
           if v != b[i] {
                return false
            }
         }
          
        func equalReflect() bool{
            return reflect.DeepEuqal(a,b )
        }
    
    ```
## Q7 What different  between %v and %+v

    ```go

        type Test struct{
            TestName string
        }
        

        log.Printf("%+v",test) { jiangyuhuang}
        log.Printf("%+v",test) { name:jiangyuhuang}

    ```

## Q8 what is Iota

      It is like jave of enum.
      ```
      
      const (
	    FlagNone BitFlag = 0
	    FlagRed          = 1 << iota // 1 << 0 = 1
	    FlagGreen                    // 1 << 1 = 2
	    FlagBlue                     // 1 << 2 = 4
        )
    ```

# summary
  lt's base knowledge in golang,right ?



    

    





