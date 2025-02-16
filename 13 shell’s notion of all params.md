# 13. shell’s notion of all params

- in shell, we have 3 important variables
    - @ - for getting all the parameters
    - “#” - for getting the number of parameters supplied to the script
    - * - for getting all the parameters
- so what’s the difference between @ and * ?
- the difference is subtle

- so when you get all arguments by *, bash thinks that the arguments are separated by space.
- and also when you put the arguments gotten by *, and put them into quotes, you get one string.
- but, when you get the arguments by @, bash interprets them like we do in programming languages for example in C, the argv array holds each argument correctly.
- so whenever you want to refer arguments, always use @.
- to demonstrate the concept, we have following code

```bash
# script invoke.sh
# script to invoke another script "printargs.sh"
echo 'invoking printargs with $*'
./printargs $*

echo 'invoking printargs with "$*"'
./printargs "$*"

echo 'invoking printargs with "$@"'
./printargs "$@"

# output #
# suppose you have following directory listing
# my car.jpg mydata mymusic mypicture
#
# ./invoke.sh my*
# echo 'invoking printargs with $*' 
# arg1 -> my, arg2 -> car.jpg
#
# echo 'invoking printargs with "$*"' 
# arg1 -> my car.jpg mydata mymusic mypicture, arg2 -> 
#
# echo 'invoking printargs with "$*"' 
# arg1 -> my car.jpg , arg2 -> mydata
```

```bash
# the script printargs.sh
printf "arg1 -> %s, arg2 -> $s \n\n" $1 $2
```

- the point of interest is, * will separate arguments by space hence we see two arguments one for `my` other for `car.jpg`
- but @ correctly parses arguments hence we see first argument `my car.jpg` and other `mydata`