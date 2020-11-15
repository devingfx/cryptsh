# cryptsh

Create crypted self-executable bash scripts.

## Usage

```bash
cryptsh <script.sh> <name>
```
Takes `script.sh`, encrypt it using openssl aes-256-cbc asking you to provide a password twice, and writes the resulting self-executable script as `name` (or default name: `secure`).

```bash
$ cat exemple.sh
#!/bin/bash
echo "Secure script had this arguments: $@"

$ ./cryptsh exemple.sh omg.nope
enter aes-256-cbc encryption password:
Verifying - enter aes-256-cbc encryption password:

$ cat omg.nope
#!/usr/bin/env bash
aZ=s aX=t aY=b aR=r aS=e aP=, aQ=- aV=x aW=1 aT=. aU=p aJ=d aK=a aH=c aI=5 aN=3 aO=6 aL=k aM=o aB=2 aC=u aA=l aF=m aG=n aD=i aE=f
$aH$aK$aX "$0"|$aZ$aS$aJ "$aW$aP$aN$aJ">"$0$aT$aZ";$aM$aU$aS$aG$aZ$aZ$aA $aS$aG$aH $aQ$aJ $aQ$aK$aS$aZ$aQ$aB$aI$aO$aQ$aH$aY$aH $aQ$aU$aY$aL$aJ$aE$aB $aQ$aD$aG "$0$aT$aZ" $aQ$aM$aC$aX "$0$aT$aJ" && $aR$aF "$0$aT$aZ" && $aT "$0$aT$aJ" "$@";$aS$aV$aD$aX
Salted__2X/^F  n^Uq\ ^pfT
,/ 7^f^@w)  -t :  |^e    ^D0Ym^X   ?Z ^Y^V 98  Pq^w^L( ^a ^EA      j L  ^MG^Ub  =^NX}^D%]

$ ./omg.nope some args passed
enter aes-256-cbc decryption password:
Secure script had this arguments: some args passed

$
```
