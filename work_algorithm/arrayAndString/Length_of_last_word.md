# Length of Last Word

 ...
 
 ```go
    func lengthOfLastWord(s string) int {
    s=strings.Trim(s," ")
    val:=strings.Split(s," ")
    return  len(val[len(val)-1])
}
 ```