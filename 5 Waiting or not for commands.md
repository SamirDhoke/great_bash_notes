# 5. Waiting or not for commands

- some commands takes very long to complete after running them.
- what happens internally is, all commands when ran, run in same process queue, but the shell waits for each command to complete by default.
- so, ls command completes very fast while some command may not complete that fast, but the shell will continue to wait for its completion and will not give prompt back to the user.
- to make the shell not wait for the command to complete (the command will still be running in the process queue) and get the prompt back, we have a mechanism in unix.
    - `./commandTakingTooLong.sh &` the & tells the shell to not wait for this command and give the prompt back to user.
- when adding & after the command, it will return the job ID and the process ID of the command.
- to run multiple commands in the same line, you can use the ; delimiter
    - `./commandTakingTooLong.sh & ; ./someOtherCommand &`
- now, once you have told the shell to not wait for the command by adding &, you can also tell the shell to wait for the command.
    
    ```bash
    
    ./commandTakingTooLong.sh &
    [1] <PID>
    #> pwd
    <current path>
    #> wait <PID> -- this will put the shell waiting for the command to complete and will not give prompt back.
    ```
    
    you use just `wait` i.e. without any PID and it will **wait for all** the commands executed with & so far