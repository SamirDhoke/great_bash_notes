# 16. reading input from user

- to read input from the user, we have a read command in bash.
- this read command will block the script/shell and ask the user for the input.
- it will return 0 when it completes reading one line.
- it will return 1 when it encounters EOF.
- example
    
    ```bash
    #!/bin/bash
    
    # read from user, block the current shell
    read VAR # read the data into the variable VAR
    echo $VAR
    ```
    
- now, `ls -l | read VAR` does not work, because commands from the pipelines are executed in sub-shells.
- example 1 : reading the response of user
    
    ```bash
    #!/bin/bash
    
    read -p "Enter your answer : " VAR
    
    if [ $VAR="y" ]
    then
            echo "positive";
    else
            echo "negative"
    fi
    ```