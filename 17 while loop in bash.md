# 17. while loop in bash

- while loop in bash is like in any other programming language.
    
    ```bash
    while <expression>
    do
    	<commands>
    done
    ```
    
- after the last command in the body of the while loop, the expression will get evaluated, and based on the return value of this expression, bash decides to enter the loop or break the loop.
- we can use same (( )) double parenthesis to perform numeric operations inside of it and return the output.
- example 1: printing integers upto a number
    
    ```bash
    #!/bin/bash
    
    NUM=$1
    let i = 0;
    while (( i < $1 ))
    do
    	echo $i;
    	let i += 1
    done
    ```
    

- the let keyword is just a syntactic sugar for (()). let and (()) are exactly same.
- while will continue running till it receives the value 1 (which in bash is a false, 0 is true)
- so, we can group while with read to keep reading input from user till the user gives EOF signal (Ctrl + D).
- example 2: reading from user
    
    ```bash
    # script readinput.sh
    while read VAR # only exits when received EOF
    do
    	echo "file name : $VAR";
    done
    ```
    
    ```bash
    $> ls -l | readinput.sh 
    ```