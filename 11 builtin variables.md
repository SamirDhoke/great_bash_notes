# 11. builtin variables

- bash has some built in variables that are quite useful for our scripting purpose.
- we know the if statement in bash checks if the command successfully completed or not and it checks that by checking the exit status of the process.
- the `?` variable of bash holds the exit status of the most recently executed command.
- we can use that to decide whether to continue executing further commands or not.
- another builtin variable is `PS1`. it holds the prompt string for the bash prompt.
- another variable is the `PATH`, it holds the paths separated by :
- whenever a command is executed without its absolute path, the shell checks if the command exists in any of the paths present in PATH from left to right.