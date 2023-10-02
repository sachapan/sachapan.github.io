---
layout: post
title:  "linux misc. command snippets"
date:   2023-10-02 09:04:51 -0400
categories: tech linux 
---

# Linux command line-fu

Some/many of these are quite dated but I preserve them nonetheless.


## xargs dealing with spaces

Specify the delimiter as only newline.

`xargs -d "\n"`

## Find all symlinks.

Useful if, for example, you destroyed all of them on a filesystem you were trying to migrate from one hard disk to another and now you need to recover them from the backup that you did take before being an idiot:

`find / -type l -exec ls -l {} \;`

When copying from one volume to another:

`cp -ax /<source> /<destination>`

## Copy MBR with and without partition table

`dd if=/dev/hda of=/dev/hdb bs=512 count=1`
`dd if=/dev/hda of=/dev/hdb bs=446 count=1`

## Remove all non-current kernel packages on Ubuntu:

`dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge`

## Monitor progress of dd action

`while pgrep ^dd; do pkill -INFO dd; sleep 10; done`

## sed snippet to remove blank lines and those that begin with a digit, and finally deal with unix2dos carriage return monkey business.

`sed ''/^$/d /^[0-9]/d s/\r//g' < input.txt > output.txt`

