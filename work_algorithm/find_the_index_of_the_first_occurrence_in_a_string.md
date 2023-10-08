# Find the Index of the First Occurrence in a String





simple O(0)
```go

func strStr(haystack string, needle string) int {
     if len(needle)==0{
         return -1
     }
     preChar:= needle[0]
    for i:=0;i<len(haystack);i++{
        if  preChar== haystack[i] &&  len(haystack)-i >= len(needle){
            pass :=true
            for j:=0;j<len(needle);j++{
               if haystack[i+j] != needle[j]{
                    pass=false
                    break
               }
            }
            if pass{
                return i 
            }
        }
    }
    return -1
     
     
}
```