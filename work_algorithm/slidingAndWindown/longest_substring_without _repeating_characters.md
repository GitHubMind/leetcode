#  Longest Substring Without Repeating Characters

tip: map and sliding window~



```go
func lengthOfLongestSubstring(s string) int {
    m:= map[byte]int{}
    n:=len(s)

   
    r,l,ans :=0, 0,0 
    for l< n {
        if l !=0{
            delete (m,s[l-1])
        }
        for r < n && m[s[r]] ==0  {
         m[s[r]]++
         r++
        }
        l++
        ans =max(ans,r-l+1)
    }

 
   return ans
}

func max(a,b int) int{
    if a>b{
        return a
    }
    return b
}
```
     