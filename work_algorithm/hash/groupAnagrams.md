# Group Anagrams



```go
    func groupAnagrams(strs []string) (result [][]string) {
   
    numberMap :=map[string][]string{}
    for i:=0;i<len(strs);i++{
         s :=[]byte(strs[i])
         sort.Slice(s,func(i,j int )bool { return s[i]<s[j] })
         sortedStr := string(s)
         numberMap[sortedStr]=append(numberMap[sortedStr],strs[i])
    }
    for _, r :=range  numberMap {
        result =append(result,r)
    }
    return

}
```