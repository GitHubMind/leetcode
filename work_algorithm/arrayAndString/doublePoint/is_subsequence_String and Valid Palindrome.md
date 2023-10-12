
# Valid PalinDrome


## base binary search

```go
func isPalindrome(s string) bool {
   s = strings.ToLower(s)
    L:=0
    R:=len(s)-1
    for L<R{
        
        for L<R && !isalnum(s[L]){
            L++
        }

            
        for  L<R && !isalnum(s[R]){
            R--
        }

        if L<R{
             if s[L] != s[R] {
                return false
            }
            R--
            L++

        }
     
    }
    return true
}

func isalnum(ch byte) bool {
    return (ch >= 'A' && ch <= 'Z') || (ch >= 'a' && ch <= 'z') || (ch >= '0' && ch <= '9')
}
 

```

# is Subsequence
## false/slow point

```go
    func isSubsequence(s string, t string) bool {
   
    i, j := 0, 0
    for i < len(s) && j < len(t) {
        if s[i] == t[j] {
            i++
        }
        j++
    }
    return i == len(s)
 

}
```