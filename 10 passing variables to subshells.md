# 10. passing variables to subshells

- previously, we saw that variables created in one instance of bash shell remain in that instance and is not accessible to subshell or parent shell.
- to overcome this shortcoming, we can make the variables global (called environment variables).
- to make the variable global you have to export it by running
    - `export VAR`
- now, it will available to all the instances of bash in the OS.
- you can change the value of VAR (or any exported variable) **in the shell where you exported it**, and the modified value will reflect everywhere its being read in.