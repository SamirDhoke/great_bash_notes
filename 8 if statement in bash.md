# 8. if statement in bash

- if statement works in following way
    
    ```bash
    if [ <condition returns good output> ]
    then
    	<command 1>
      <command 2>
      <command n>  
    else
      <command a>
      <command b>
      <command z>  
    fi
    ```
    
- what does returning good output means ?
- each command return 0 if everything went fine and > 0 if something went wrong during its execution.
- the if statement looks at this return value and decides whether the command returns good output or not.
- we, ourselves can return the output in bash by the exit statement.
    - `exit <value>` for example: exit 0, exit 1, exit 100
- our script can now be written like this
    
    ```bash
    #! /bin/bash
    # Clear the contents of /tmp
    
    if [ cd /tmp ]
    then
    	rm *
    	echo "removed temp files successfully"
    else
    	echo "directory does not exist. Exiting..."
    	exit 1
    exit # without any code followed by exit, it return with 0 by default
    ```
    

**Advanced**

- the [] after if is called the test command.
- so it’s basically, `if test <expression>`
- based on the return value of this test expression, the branching will take place to the `then` segment or to the `else` or `else if` segment.