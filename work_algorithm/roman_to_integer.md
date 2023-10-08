# Roman to Integer
```SHELL
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```
 You must be allowtec a rules that is IV =4, I=1 V=5  I smaller than V ,so it's combine rule.



```go
    func romanToInt(s string) int {
        romanNumerals:= map[byte]int{
            'I': 1,
            'V': 5,
            'X': 10,
            'L': 50,
            'C': 100,
            'D': 500,
            'M': 1000,
            }
        ans:=0
    for i:=0;i<len(s)-1;i++{
        val := romanNumerals[s[i]]
        if val < romanNumerals[s[i+1]]{
            ans -=val
        }else{
            ans += val
        }
    }
     
    return ans+romanNumerals[s[len(s)-1]]
    }
```