#  longest common  prefix

 Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

### 


```go

    func longestCommonPrefix(strs []string) string {


    if len(strs) ==0 {
        return ""
    }

    prefix := strs[0]
    count  := len(strs)
    for i :=1 ;i <count;i++{
             
            minlen:= min(len(prefix),len(strs[i]))
            index :=0
            for j:=0;j< minlen;j++{
                if   prefix[j]==strs[i][j]{
                    index++
                }else{
                    break //  TIP:
                }
            }
            prefix =  strs[i][0:index]
    }
    return prefix
    }       

    func min(x, y int) int {
        if x < y {
            return x
        }
        return y
    }

```