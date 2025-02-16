# 7. Taking actions on success or fail

- now we will learn about decision making in bash.
- before going to the actual if statement, we will learn about the shorthand operators in bash which are `&&` and `||` .
- && is the AND operator which acts in the following way
    - `<first command> && <second command>`
    - now, the expected behavior is the all commands should exit with a success status. If any one of them exits with a bad status (fails) then it will not run commands after it. (That’s how AND works).
    - so, if <first command> fails, <second command> will not run and the next line will start executing.
- || is the opposite of &&, and acts in following way
    - `<first command> || <second command>`
    - if the first command exits with a success status, further commands are not run, because the condition has been satisfied.
    - if the first command fails, it will run further commands till any one them exits with a success status and it will stop executing commands from that step.
- how is this useful ?
    - suppose you have a script where you need to make a decision based on if some command fails or succeeds.
    
    ```bash
    #! /bin/bash
    cd /tmk #tmk does not exist
    rm *
    ```
    
    - what will happen is, cd command will fail and the shell will be in present working directory
    - after that rm * will execute deleting all the files in pwd.
    - instead we can do this
    
    ```bash
    #! /bin/bash
    cd /tmk && rm * # if cd fails, further commands are not executed.
    ```
    
- another way to control the flow is as below
    
    ```bash
    #! /bin/bash
    cd /tmk 2>/dev/null || echo "cd failed, directory does not exist"
    echo "continuing on"
    ```
    

- now, one detail about grouping commands : the following syntax does not groups the commands after the `||`
    - `cd /tmk 2>/dev/null || echo "cd failed, directory does not exist" ; exit`
    - because the delimiter ; separates commands at statement level, its thinking `cd /tmk 2>/dev/null || echo "cd failed, directory does not exist"` is one statement and after that `exit` will run.
- in such cases, where we want to run `echo "cd failed, directory does not exist" ; exit` after `||` we need to group them.
    - we can group commands in unix in two ways
        - {} curly braces : when grouping with curly braces the grouped commands will run in the same shell.
            - `cd /tmk 2>/dev/null || { echo "cd failed, directory does not exist" ; exit }`
            
            ```bash
            #! /bin/bash
            cd /tmk 2>/dev/null || { echo "cd failed, directory does not exist" ; exit }
            echo "continuing on"
            
            # output will be as follows
            # cd failed, directory does not exist
            ```
            
        - () round braces : when grouping commands with round braces, the commands inside runs in a sub-shell
            - `cd /tmk 2>/dev/null || ( echo "cd failed, directory does not exist" ; exit )`
            
            ```bash
            #! /bin/bash
            cd /tmk 2>/dev/null || ( echo "cd failed, directory does not exist" ; exit )
            echo "continuing on"
            
            # output will be as follows
            # cd failed, directory does not exist
            # continuing on
            ```
            
            - this is due to cd and exit are running in sub shell and since exit will exit from the sub-shell, the current shell will keep executing next commands.