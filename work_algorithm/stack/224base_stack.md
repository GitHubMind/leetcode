224. Basic Calculator

```
Given a string s representing a valid expression, implement a basic calculator to evaluate it, and return the result of the evaluation.

Note: You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as eval().

 

Example 1:

Input: s = "1 + 1"
Output: 2
Example 2:

Input: s = " 2-1 + 2 "
Output: 3
Example 3:

Input: s = "(1+(4+5+2)-3)+(6+8)"
Output: 23

```golang
func calculate(s string) int {
	res := 0
	stack := make([]int, 0, len(s))
	sign := 1
	num := 0

	for i := 0; i < len(s); i++ {
		switch s[i] {
		case '0', '1', '2', '3', '4', '5', '6', '7', '8', '9':
			num = 0
			for ; i < len(s) && s[i] >= '0' && s[i] <= '9'; i++ {
				// Calculate the total ,
                // 110 +1
				num = 10*num + int(s[i]-'0')
			}
			i--
            // summary the total
			res += sign * num

		case '-':
			sign = -1
		case '+':
			sign = 1

		case '(':
            //markdown about calcuate and sign
			stack = append(stack, res, sign)
			res = 0
			sign = 1

		case ')':
            //include operational symbols and positive and negative symbols of numbers
			sign = stack[len(stack)-1]
			val := stack[len(stack)-2]
            //The value is completely calculated
			stack = stack[:len(stack)-2]

			res = (sign)*res + val
		}

	}
	return res
}
```