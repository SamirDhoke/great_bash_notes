# 4. Here document

- here document allows you to supply an input to a command like the < operator.
- but here document accepts one argument, we call it terminator, which when found in the supplied input, will end/close the input stream.
- for example,
    - `wc << EOF` , here EOF is the terminator
    - now, the shell will open the input stream and will continue accepting input till it encounters EOF.
    - you can give any string in place of EOF, but EOF is a convention.
- full example:
    
    ```bash
    wc << EOF
    > Hi this is a line
    > this is another line
    > EOF
    2 9 30
    ```
    
    ```bash
    grep -i bill << EOF
    > john 555-123
    > juan 555-453
    > nancy 555-643
    > bill 555-4343
    > EOF
    bill 555-4343
    ```