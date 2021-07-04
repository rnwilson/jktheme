---
layout: post
title: "error: gpg failed to sign the data"
subtitle: "Commit with your cryptographic signature"
date: 2021-07-04
categories: [Programming]
---
![Bash Syntax Error](https://raw.githubusercontent.com/rnwilson/rnwilson.github.io/6bf00e9c6675714d916a73a81523c8d8bf696133/img/carbon(2).png)

```
ubuntu@srv1:~/random-repo$ export GPG_TTY=$(tty)
ubuntu@srv1:~/random-repo$ echo "test"  | gpg --clearsign
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA512

test
-----BEGIN PGP SIGNATURE-----
hbxfqzXVl/J5E5wS46EwpLQ764W79b1ZK7IU992dz9/VNTmoBueNqWjPqUBqVtCC
EIbzpioYPrd2bNQvL0rVC/y8TTAO6lHS4LbNFwyrVdMXiZEoio+80iZGiwMVx/t2
Sfc9yKz7oHGG7G3CekBu/WwJuYSE3LN50AYsI1OjMw3YmMIuCf3u6y1zXty5jZXp
GWBVXmWl3mzWU926J/YxbMIgY4exTwlnP3uyNWZ4RCnURKrOGWXhWOfs1fb3DjYr
B9O+k62vXiDKvU8wd8FzCyqjOjvtmnza87ndLnTEx4LDsgdPUPScywhAcPuh6nn+
EPuRhYYIdWjGiElSfDFne45SK6YX+i0/IQdi4YPK+ITbFA27CQQ=
=EDl5
-----END PGP SIGNATURE-----
ubuntu@srv1:~/random-repo$ git config -l | grep gpg
ubuntu@srv1:~/random-repo$ gpg --list-secret-keys --keyid-format=LONG
/home/ubuntu/.gnupg/pubring.kbx
-------------------------------
sec   rsa4096/__A0D7D3FF0A87705E__ 2021-05-24 [SC] [expires: 2037-05-20]
uid                 [ultimate]
ssb   rsa4096/4C98B5E642638680 2021-05-24 [E] [expires: 2037-05-20]
ubuntu@srv1:~/random-repo$ git config --global user.signingkey __A0D7D3FF0A87705E__
ubuntu@srv1:~/random-repo$ git add .
ubuntu@srv1:~/random-repo$ git commit -S -m 'Updates'
[main 5c918b6] Updates
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 del
ubuntu@srv1:~/random-repo$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 985 bytes | 985.00 KiB/s, done.
```
