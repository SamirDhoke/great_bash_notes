# 9. variables in bash

- variables are containers for values.
- in bash, variable names can start with alphabet and can include letter or underscore.
    - `VAR=”this is a string”` - this is how you set a variable in bash
    - `echo $VAR` - prefixing the variable name with $ will tell bash to evaluate this variable and get its value. This is called substitution of variable with their values. Bash will scan the statement for $ and if it encounters it, it will substitute the variable with its value before executing the statement.
- you can concatenate the output of variable with some other string
    - `echo Hello ${VAR} nice to meet you`
- you can use variable substitution in commands as well
    - `VAR=Documents`
    - `ls $VAR`
- what happens if the variable does not have any value → it returns nothing or empty value.
- **now, variables defined in a shell remains to that shell, they are not visible to subshells or parent shell.**