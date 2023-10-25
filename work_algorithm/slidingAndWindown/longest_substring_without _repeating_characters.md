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
     
seceond code:
```go

    func lengthOfLongestSubstring(s string) int {
     mm := make(map[byte]int, 0)
    l, r := 0, 0
    n := len(s)
    ans := 0
    for r < n {
        if val, ok := mm[s[r]]; ok && val >=l{
            l=val+1
        }
        mm[s[r]]=r
        ans=max(ans,r-l+1)
        r++

    }
    return ans

}
func max(a,b int)int{
    if a<b {
        return b
    }
    return a 
}

```