# Evaluate Reverse Polish Notation

# tip:
        don't have intertial thinking 
        You can use strconv to judge whether the string is a numbe or not
# code 

```go
    func evalRPN(tokens []string) int { 
    stack := []int{}:
    for _,token := range tokens{
        //直接过滤不是整数
         val,err := strconv.Atoi(token)
         if err ==nil{
                 stack =  append(stack,val)   
         } else{
        //然后提取stack中 最后两个数字 ? 为啥

             num1, num2 := stack[len(stack)-2], stack[len(stack)-1]
            stack = stack[:len(stack)-2]

 
            //拿出来然后去做判断
                switch token{
                    case "+":
                    stack = append(stack, num1+num2)
                case "-":
                    stack = append(stack, num1-num2)
                case "*":
                    stack = append(stack, num1*num2)
                default:
                    stack = append(stack, num1/num2)
                } 
            }
         } 
    //因为第一个数可以获得最后两个
    return stack[0]
}

```