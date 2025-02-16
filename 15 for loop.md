# 15. for loop

- in bash, we can write for loop like this
    
    ```bash
    for VAR in one two three # one two three can be anything, in this case, its strings one two and three.
    do
    	echo $VAR;
    done
    ```
    

- if you do not give iterables after the “in” clause, it will iterate over the arguments passed to the script.
- example:
    
    ```bash
    for VAR # iterates over the arguments passed to the script.
    do
    	echo $VAR;
    done
    ```
    

- iterating over the integers
- to iterate over the integers, we have to make use of numeric operator in bash.
- (( <oprations> )) — anything inside double brackets in bash is treated as numeric operations meaning that we can do arithmetic and logical operations inside these brackets.
- example:
    
      
    
    ```bash
    for (( i=0; i<10; i++ ))
    do
    	echo $VAR
    done
    
    # prints out integers from 0 to 9, each on new line.
    ```
    
- but to reference variables declared, we need to use the $ sign inside these brackets.
- now, we need to discuss 2 special characters in bash
    - “#” —> when we use hashtag at the end of a variable, we are saying to remove the starting characters that matches a pattern.
        - but when used at the front of a variable, we are telling bash to get its length and not the actual value.
        - so, #VAR will get substituted to the integer value representing the length of the string inside this variable.
    - “:” —> this variable is used to get a substring.
        - the syntax to use it is <variable>:<start index>:<number of characters from the index>
        - example
            
             
            
            ```bash
            VAR="hi, my name is anthony"
            echo ${VAR:1:4}
            # outputs i, m
            # i.e. it takes the 4 characters starting at index 1.
            ```
            
- example 1 : printing each character of the argument
    
    ```bash
    STRING=$1;
    CHAR=''
    for ((i=0; i<${#STRING}; i++))
    do
    	CHAR=${STRING:$i:1}
    	echo $CHAR
    done
    ```
    
- example 2 : reversing the argument string
    
    ```bash
    STRING=$1;
    CHAR=''
    REVERSED=''
    for ((i=0; i<${#STRING}; i++))
    do
    	CHAR=${STRING:$i:1}
    	# echo $CHAR
    	REVERSED="${CHAR}${REVERSED}"
    done
    
    echo $REVERSED
    ```