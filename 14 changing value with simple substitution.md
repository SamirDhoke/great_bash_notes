# 14. changing value with simple substitution

- one of the ways to do substitution and then operations on the substituted value in bash is as follows
    
    ```bash
    # ${VAR<operations>}
    # for example
    VAR=dynamo:/tmp/file.txt
    echo ${VAR%:*}
    # output is dynamo
    echo ${VAR#*:}
    # output is /tmp/file.txt
    ```
    
- % in bash is used to remove characters at trailing end. The syntax to use % is
    
    `<string>%<pattern>`
    
- it will remove the characters that matches the pattern from the trailing end.
- similarly # in bash is used to remove characters from the starting end.
    
    `<string>#<pattern>`
    
- in above example, we used the wildcard character in bash to tell it to match 0 or more than 0 occurrences of any character.
- we have several special characters in bash like ? (to match 1 character), *(to match 0 or more characters), etc.
- a single % or # matches the smallest possible match.
- a double %% or ## matches the longest possible match.
- for example:
    
    ```bash
    VAR=abba
    echo ${VAR%*a}
    # output is abb
    echo ${VAR%%*a}
    # output is empty string, because it will match the entire string.
    ```
    
- one more special character in bash is the forward slash (/)
- it does the job of find and replace.
- example
    
    ```bash
    VAR=abba
    echo ${VAR/bb/tacam}
    # output is atacama, bb is replaced by tacam.
    
    ```
    
- one more use of this character is that you can delete the pattern from the string. Its similar to ${VAR/<pattern>/<empty_string>}
    
    ```bash
    VAR=abba
    echo ${VAR/bb}
    # output is aa, bb is deleted
    ```