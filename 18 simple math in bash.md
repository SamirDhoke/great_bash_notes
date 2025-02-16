# 18. simple math in bash

- if we try to do following in bash, we will not get the expected functionality
    
    ```bash
    A=1
    B=2
    C=A+B # C is literally equal to A+B
    C=$A+$B # C is equal to 1+2
    let C=A+B # now C is equal to 3
    ((C=A+B)) # C is equal to 3
    C=$((A+B)) # C is equal to 3
    ```
    
- let <expressions> evaluates the arithmetic expression and also it will do necessary substitution in place of variable values to correctly evaluate it.
- ((<expression>)) is the same thing as let, but without the let keyword.
- $((<expression>)) is a bit different, it will refer to the value of the expression.