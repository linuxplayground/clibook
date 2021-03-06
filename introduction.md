# Introduction

CLI for beginners is a simple booklet style guide to writing effective and maintainable command line interface scripts. While the examples in this book are for \*nix environments, the principals can be applied to scripts written for any environment.

```bash
#!/usr/bin/env bash
# Hello, World!
echo 'Hello, World!\n'
```

# How To Use This Book

Each section is sufficiently self contained so that you can jump to any part and follow the tutorial from the start to the end.

All code snippets have been tested on a simple vagrant virtual machine.  In some cases, more than one virtual machine will be required to run the examples.  This will be true from the moment we start exploring remote CLIs.

# Prerequisites

* \*nix system.  Any linux with the Bourne Again Shell or Mac or even Windows Ubuntu Bash.  Although I don't pretend to know if vagrant will work in this environment.

* Vagrant

* Virtualbox \(For Vagrant\)

* An internet connection so you can download the vagrant box.


## Getting Set Up

Make sure you have vagrant, git and curl set up on your machine:

```bash
$~ sudo apt-get install vagrant git curl
```

Clone the book repository:

```bash
$~ git clone git@github.com:linuxplayground/clibook-code.git
$~ cd clibook.git
$~ vagrant up clibook --provider virtualbox
```



