# 3. Pipe

- piping the output is the equivalent of following
    - `ls -l > /tmp/lsout.txt`
    - `wc < /tmp/lsout.txt`
- instead of creating the temp file and then removing it after its use is over, we can do the pipe
    - `ls -l | wc`
    - it will make the stdout of ls -l, the stdin of wc
    - the stdout of wc is kept as it is.
- now, what if we want to redirect the stderror to stdout as will with the pipes,
- if we do it like previously ls -l | 2>&1, it will not work because in case of pipes, linux expects start of new command after the pipe.
- so to redirect the stderror to stdout in case of pipes, we put it before the pipe. This is only spacial case of the order linux can allow.
    - `ls -l 2>&1 | wc`