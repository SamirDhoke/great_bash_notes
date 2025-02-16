# 12. formatting output with printf

- printf is a command used widely with different names in different programming languages.
- print in python, console.log in js, cout in c++, println in java, etc.
- its like echo but it allows us to do string formatting.
- string formatting involves two things
    - one is the placeholder string
    - other is the actual value for this placeholder.
- the syntax of printf is very simple :
    - `printf “<string with placeholders>” value1 value2 value3 … valueN`
- some of the placeholders
    - all placeholders starts with % sign.
    - %d - format decimal value
    - %f - format floating point values
    - %s - format string value
    - %x - format hex value
    - %% - this is special case when you want to print the % sign itself.
- examples :
    
    ```bash
    MYVAR=John
    printf "Hi, %s, Nice to meet you !" $MYVAR
    ```