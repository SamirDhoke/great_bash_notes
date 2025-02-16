# 2. I/O redirection

- the redirection operators (<, >)
- > will redirect the output stream by default to whatever you will provide.
    - for example, `ls -l > lsout.txt` will redirect the output stream for the ls command to the lsout file instead of stdout.
- now, it will not redirect the stderror as well. stderror still points to stdout. To redirect stderr to another file you can use the command like this
    - `ls -l > lsout.txt 2> lserror.txt` the 2 here represents the stderror stream value.
- to redirect both stdout and stderr to same file, you can use several ways
    - `ls -l &> lsout.txt` this will tell the bash to redirect stderr and stdout to same file.
    - `ls -l > lsout.txt 2>&1` this tells bash two things
        1. redirect the stdout of ls -l to lsout.txt
        2. and, redirect the stderr to the modified stdout.
        
        Here, order matters, if you put 2>&1 first, like this `ls -l 2>&1 > lsout.txt`, it will first redirect the stderr to stdout which is still the terminal (as its not modified) and after this it will redirect the stdout of ls -l to the lsout.txt file (now its modified). So, stderr will still be pointing to terminal and not the file.
        
- < will redirect the stdin of a process. There are two ways a command expects input
    - through arguments passed to it
    - through the stdin (when the programs halts and you get the control to type something)
    - with < you can provide input to the second way of passing input to a command.
    - for example:
        - `wc` when invoked without any argument, reads from stdin till user presses ctrl+b and then it will count the lines, words, and characters of this text.
        - `wc < lsout.txt` will change the stdin of wc from the terminal to the file and wc will behave as if the contents of lsout.txt were put into the stdin.