# Structure Of A CLI

Every CLI has a similar structure.  They are as follows:

## The Interpreter Declaration

The shell environment will read the very first line of the script to determin which interpreter it should invoke your script with.  This line is optional because it is possible to execute scripts by passing them as an argument to the interpreter you need.  For example:

```bash
#!/usr/bin/env bash
echo 'Hello, World!'
```

Save this script as, `hello1.sh`, set the execute bit on the file permissions and execute it.

```bash
$~ chmod +x hello.sh
$~ ./hello.sh
Hello, World!
```

Or you can try a simpler, shorter version of the script which your users will need to magically know which interpreter to use.

```bash
echo 'Hello, World!'
```

Save this script as hello2.sh and execute it by passing the file name as an argument to the bash interpreter.

```bash
$~/ usr/bin/bash hello2.sh
Hello, World!
```

The path to Bash on your system \(if you are not using the Vagrant image\) might be different.  It is precicly because of this reason, that we use `#!/usr/bin/env bash` in the interpreter declaration.  It instructs the system to find the interpreter and use it.

