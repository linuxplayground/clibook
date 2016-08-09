# Comments

There are some simple rules around commenting that will help to decide what should be included.

* Always provide a simple description of the script at the top.

* Comment tricky, non-obvious, interesting or important parts of your code.

* Don't comment everything. If there's a complex algorithm or you're doing something out of the ordinary, put a short comment in.


In BASH comments are any line beginning with a `#`

For example:

```bash
#!/usr/bin/env bash
# Serve beer only if person is 18 or over.
echo "Hi, I am your barman."
...
```

Here is an example showing a comment in a python script that explains why a piece of logic has been implimented.  It does not detail the logic itself as that's self explanitory.

```py
# For some reason MFT confuses the meaning of ORDER. 
if args.order == 'ASC':
  args.order = 'DESC'
else:
  args.order = 'ASC'
```



