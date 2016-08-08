## Types Of CLI

Shell interfaces have changed in purpose over the years. Changing technologies and architectures have warrented different approaches to problem solving by CLI.

### The Application Installer

In this mode, CLI authors have written scripts to allow installation of applications on headless servers. The intention is usually to support "unattended" installation of software.

```
$~ sudo apt get install curl
```

### Local Automation Tools

Here, a CLI is deployed to a server and it interacts with local filesystems and applications via exposed interfaces to enable automation. Types of automation might be:

* Generate a report from the application or operating system.
* Modify the operating system. IE: manage user accounts, alter local security settings

```
$~ awk -F: '($1 > 1000) { print $3 }' /etc/passwd
```

### Remote OS Automation Tools

A remote OS CLI uses the Secure SHell \(SSH\) to interact with remote software and operating systems.


```
$~ ssh davidl@192.168.0.10 "df -h"
```

### API Automation

Most recently, CLI Tools are used to interact with APIs exposed by SaaS and PaaS providers to execute any number of functions on remote systems. For example, the AWS \(Amazon Web Services\) exposes a rich API for managing all the available cloud resources they offer.

```
$~ curl -XGET \
    -H 'Content-Type: application/json' \
    -H 'Authorization: basic ZGF2aWRsOnBhc3N3b3JkCg==' \
    https://api.example.com/v1/resource
```



