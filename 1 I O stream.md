# 1. I/O stream

- when bash invokes/executes command, 3 streams are passed to it
    - STDIN (0), STDOUT (1), STDERROR (2).
    - the number represents the actual value of the stream.
- the bash/shell can change the values of each stream to point to different things like, stdout can be pointed to a file to write to it or stdin can be pointed to a file to read from it.
- we can also do this change and this change is called I/O redirection. There are couple of ways to do it.