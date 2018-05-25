---
Date: May 25, 2018
Topic: Apache2
---

# 403 Forbidden Error on Apache2

A 403 Forbidden Error occurs when static files are uploaded via FileZilla. Reasons for this error are permissions or .htaccess error.

## Default Permissions

Chances are that default permissions can be modified in FileZilla. But for now I'll just fix this problem in the terminal.

## Permissions

> Directories and folders must be 755. Executable scripts within the cgi-bin folder must be 755. Images, media, and text files like HTML should be 755 or 644.

```
chmod 755
chmod u=rwx,go=rx
```

```
chmod 644
chmod u=rw,go=r
```

Here is a simple explanation:

```
Symbolic:   rwx r-x r-x   |  000 = 0
Binary:     111 101 101   |  001 = 1
Decimal:     7   5   5    |  010 = 2
                          |  011 = 3
Symbolic:   rw- r-- r--   |  100 = 4
Binary:     110 100 100   |  101 = 5
Decimal:     6   4   4    |  110 = 6
                          |  111 = 7
Owner/Group/Others
```

## Other Possible Problems

## Solution

Since the website I am working on is a very basic subdomain site. I ignored all other details and assigned all the files or directories with permisssion 755. This fix the problem well. But further configurations are requeired to secure Apache from other threats.

```
chmod 755 -R directory
chmod 755 file
```

## Related Links

* 403 Error: https://support.hostgator.com/articles/specialized-help/403-forbidden-or-no-permission-to-access/

* Secure Apache: https://www.techrepublic.com/blog/10-things/10-things-you-should-do-to-secure-apache/
