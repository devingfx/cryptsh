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
cat "$0"|sed "1,2d">"$0.s";openssl enc -d -aes-256-cbc -pbkdf2 -in "$0.s" -out "$0.d" && rm "$0.s" && . "$0.d" "$@";exit
Salted__2X/^F  n^Uq\ ^pfT
,/ 7^f^@w)  -t :  |^e    ^D0Ym^X   ?Z ^Y^V 98  Pq^w^L( ^a ^EA      j L  ^MG^Ub  =^NX}^D%]

$ ./omg.nope some args passed
enter aes-256-cbc decryption password:
Secure script had this arguments: some args passed

$
```
