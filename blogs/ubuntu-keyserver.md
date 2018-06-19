---
Date: May 30, 2018
Topic: Ubuntu
---

# Error When Adding Keyserver

## About

When I tried to install typora on ubuntu, adding repository would fail if a special keyserver is not added. We should add a keyserver first:

```
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ...
```

However, for some reasons the would return the error as below:

```
gpg: keyserver receive failed: Server indicated a failure.
```

## Solutions

I don't know how the whole keyserver works, but by changing the port to 80 solves the problem.

```
$ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys ...
```

I'll leave the problem here for now.

## Related Links

* gpg: keyserver receive failed: https://unix.stackexchange.com/399027/gpg-keyserver-receive-failed-server-indicated-a-failure
