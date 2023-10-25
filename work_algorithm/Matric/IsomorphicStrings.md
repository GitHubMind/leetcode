#Isomorphic Strings

```
func isIsomorphic(s string, t string) bool {

    if len(s)<1 || len(t)<1|| len(s)!=len(t){
        return false 
    }

    sm := map[byte]byte{}
    tm := map[byte]byte{}
    for i:= range s {
        x,y := s[i],t[i]
        //double reflect
        if  (sm[x]>0 && sm[x]!=y) || (tm[y]>0 && tm[y] !=x){
                return false
        }
        // pass test case 
        //s "foo"
        //t "bar"
        sm[x]=y
        tm[y]=x

    }

    return true
}
```