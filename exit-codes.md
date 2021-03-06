# Exit Codes

Exit codes are used in CLI scripts to know the execution result.  All the standard GNU tools available emit exit codes on completion of failure that provide a hint as to the execution result.

To find the exit codes for a particular command you can start with the manual for that tool.  For example in the manual for `grep` \(`~$ man grep` \)

```
EXIT STATUS
  The exit status is 0 if selected lines are found, and 1 if not found. If an error occurred the exit status is 2. 
  (Note: POSIX error handling code should check for '2' or greater.)
```

## Testing for Exit Codes in Bash

Bash records the exit code of the last command ran in the variable: `?`

For example:

```
~$ cat hello4.py | grep foo
~$ echo $?
1
~$ cat hello4.py | grep World
print('Hello, World!')
~$ echo $?
0
```

In the above example, grep exited with a status code of 1 indicating that \(according to the grep manual\) that the string was not found.  We know the string `foo` was not found because grep did not return any output.

In the second attempt, a result was found and grep exited with exit code = 0.

# Declaring Your Own Exit Codes

As CLI scripts become more complex and other developers use them in their own scripts, it becomes good practice to emit exit codes depending on the success or failure of a command to execute.  Every bash script will exit with exit code = 0 by default.

Here is an example of a simple bash script that exits with exit code = 1 on failure and exit code = 0 on success.

```bash
#!/usr/bin/env bash

# Example of script showing exit codes
# Exit = 0 for numbers above 17
# Exit = 1 for numbers below 18
# exit = 2 for no input
# exit = 3 for non integer input.

[ -z $1 ] && exit 2
[[ $1 != *[[:digit:]]* ]] && exit 3
[ $1 -lt 18 ] && exit 1 || exit 0
```

Save this file as `exit1.sh`, set it's executable permission and run it.

```
~$ chmod +x exit1.sh
~$ ./exit1.sh
~$ echo $?
2
~$ ./exit1.sh foo
~$ echo $?
3
~$ ./exit1.sh 21
~$ echo $?
1
~$ ./exit1.sh 16
~$ echo $?
0
```

Having useful exit codes that can be tested for in your scripts allows your script to be included in other scripts in creative ways.  To demonstrate this concept, lets write a script that serves beer in a bar.  The script will accept two arguments:

```
./servebeer.sh <your age>
```

The script will check your age using the `exit1.sh` script and then if all is OK, it will serve the beer.

```bash
#!/usr/bin/env bash
# Serve beer only if person is 18 or over.
echo "Hi, I am your barman."
./exit1.sh $1
ALLOWED=$?
[ $ALLOWED -eq 0 ] && echo "Your beer is served"
[ $ALLOWED -eq 1 ] && echo "Sorry 'Sir' you are too young to drink here."
[ $ALLOWED -gt 1 ] && echo "I can not tell how old you are."
```

