

Two Sum II - Input Array Is Sorted

tip:  return just two value so that don't use dp methods


```go

    func twoSum(numbers []int, target int) []int {
   
   
      l:=0
      r:= len(numbers)-1
      for l < r {
          if numbers[l]+numbers[r]== target{
                    return []int{l + 1, r + 1}
          }
           if  numbers[l]+numbers[r] < target {
               l++
             }else{

                r--
         }
     }
    return []int{-1, -1}
}
```