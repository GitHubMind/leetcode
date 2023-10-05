#  H-index

  `H-INDEX`=3,The man have 3 paper ,each of which has been cited at least 3 times.

nornol:
```go
func hIndex(citations []int) int {
     sort.Ints(citations)
    h:=0
    for i:=len(citations)-1;i>=0;i--{
          if citations[i] <=h{
            break
          }   
          h++
    }
    return h
}
```

