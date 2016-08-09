## The Interpreter Declaration



The shell environment will read the very first line of the script to determin which interpreter it should invoke your script with. This line is optional because it is possible to execute scripts by passing them as an argument to the interpreter you need. For example:



```bash

#!/usr/bin/env bash

echo 'Hello, World!'

```



Save this script as, `hello1.sh`, set the execute bit on the file permissions and execute it.



```bash

~$ chmod +x hello.sh

~$ ./hello.sh

Hello, World!

```



Or you can try a simpler, shorter version of the script which your users will need to magically know which interpreter to use.



```bash

echo 'Hello, World!'

```



Save this script as hello2.sh and execute it by passing the file name as an argument to the bash interpreter.



```bash

~$ /usr/bin/bash hello2.sh

Hello, World!

```



The path to Bash on your system \(if you are not using the Vagrant image\) might be different. It is precicly because of this reason, that we use `#!/usr/bin/env bash` in the interpreter declaration. It instructs the system to find the interpreter and use it.



In this example, you can simply set the execute bit on the file and execute it from inside a bash shell and it will work. The reason for this is because the shell assumes that the script is a bash script by default. Next try an example Python CLI to see the difference.



Create hello3.py as follows:



```

print('Hello, World!')

```



Now try to execute it directly. The execute permission is not set so we get the expected `Permission denied` error.



```

~$ ./hello3.py

-bash: ./hello3.py: Permission denied

```



Now try to set the execute bit and run the test again.



 vagrant@vagrant-ubuntu-trusty-64:~$ chmod +x hello3.py

 vagrant@vagrant-ubuntu-trusty-64:~$ ./hello3.py

 ./hello3.py: line 1: syntax error near unexpected token `'Hello, World!''

 ./hello3.py: line 1: `print('Hello, World!')'



The error is a BASH error. Bash doesn't know how to interpret this python code.



Now execute it using Python



```

~$ /usr/bin/env python hello3.py

Hello, World!

```



Finally, just for kicks alter the hello3.py script to include an interpreter declaration:



```

#!/usr/bin/env python

print('Hello, World!')

```



Save as hello4.py, set the execute permission and execute it directly.



```

~$ chmod +x hello4.py

~$ ./hello4.py

Hello, World!

```
