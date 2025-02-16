# 6. Running and commenting the script

- in order to run your script or any file in linux, it needs the executable permission on that file.
- to give a file executable permission, set the appropriate bit or use
    - `chmod +x <filename>`
- to run a script using bash, we have several options
    - bash -n <filename>
        - this option tells bash to not execute the script but to only do static analysis of syntax of the given file.
        - it will print out syntactic errors in the file.
    - bash -v <filename>
        - this tells the bash to print out each line (comments also) and also execute the commands in the script.
    - bash -x <filename>
        - this tells the bash to print out each command (not comments) as they are being executed.
- note, there is a difference between -v and -x even though the output might look same when using both the options.
- comments in bash start with #.
- any line starting with # is treated as a comment and is not executed.
- in some bash scripts, you will find the first line being
    - `#! /bin/bash` or any shell’s patch after the !
- this is to tell the OS where to find the interpreter (the shell) for this script.