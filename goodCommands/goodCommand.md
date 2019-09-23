<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Show Cal](#show-cal)
- [Show some command periodically](#show-some-command-periodically)
- [Print 50th char](#print-50th-char)
- [Batch move](#batch-move)
- [Show all line numbers in a file](#show-all-line-numbers-in-a-file)
- [Clear](#clear)
- [Encrypt bash file](#encrypt-bash-file)
- [Get URL](#get-url)
- [Get the count of a word in a file](#get-the-count-of-a-word-in-a-file)
- [Download and unzip](#download-and-unzip)
- [Get the common part](#get-the-common-part)
- [Revert a word](#revert-a-word)
- [Use less as tail -f](#use-less-as-tail-f)
- [Print a file into one line](#print-a-file-into-one-line)
- [Rename](#rename)
- [Get the file inode](#get-the-file-inode)
- [Format a file to a table](#format-a-file-to-a-table)
- [Identity an image](#identity-an-image)
- [Get cookie from firefox](#get-cookie-from-firefox)
- [Echo 256 colors](#echo-256-colors)
- [Directory diff](#directory-diff)
- [Show last n lines in a file](#show-last-n-lines-in-a-file)
- [Get 000 to 100](#get-000-to-100)
- [Fast copy or moving or someting (Detials -> Brace Expansion)](#fast-copy-or-moving-or-someting-detials-brace-expansion)
- [Searching for commands without knowing their exact names](#searching-for-commands-without-knowing-their-exact-names)
- [PWD's secrets](#pwds-secrets)
- [Insert into the first line](#insert-into-the-first-line)
- [List the command beginning with](#list-the-command-beginning-with)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

### Show Cal
    [marslo@MJ ~]
    $ cal -y | tr '\n' '|' | sed "s/^/ /;s/$/ /;s/ $(date +%e) / $(date +%e | sed 's/./#/g') /$(date +%m | sed s/^0//)" | tr '|' '\n'
                                 2014
          January               February               March
    Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa
              1  2  3  4                     1                     1
     5  6  7  8  9 10 11   2  3  4  5  6  7  8   2  3  4  5  6  7  8
    12 13 14 15 16 17 18   9 10 11 12 13 14 15   9 10 11 12 13 14 15
    19 20 21 22 23 24 25  16 17 18 19 20 21 22  16 17 ## 19 20 21 22
    26 27 28 29 30 31     23 24 25 26 27 28     23 24 25 26 27 28 29
                                                30 31

           April                  May                   June
    Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa
           1  2  3  4  5               1  2  3   1  2  3  4  5  6  7
     6  7  8  9 10 11 12   4  5  6  7  8  9 10   8  9 10 11 12 13 14
    13 14 15 16 17 18 19  11 12 13 14 15 16 17  15 16 17 18 19 20 21
    20 21 22 23 24 25 26  18 19 20 21 22 23 24  22 23 24 25 26 27 28
    27 28 29 30           25 26 27 28 29 30 31  29 30


            July                 August              September
    Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa
           1  2  3  4  5                  1  2      1  2  3  4  5  6
     6  7  8  9 10 11 12   3  4  5  6  7  8  9   7  8  9 10 11 12 13
    13 14 15 16 17 18 19  10 11 12 13 14 15 16  14 15 16 17 18 19 20
    20 21 22 23 24 25 26  17 18 19 20 21 22 23  21 22 23 24 25 26 27
    27 28 29 30 31        24 25 26 27 28 29 30  28 29 30
                          31

          October               November              December
    Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa  Su Mo Tu We Th Fr Sa
              1  2  3  4                     1      1  2  3  4  5  6
     5  6  7  8  9 10 11   2  3  4  5  6  7  8   7  8  9 10 11 12 13
    12 13 14 15 16 17 18   9 10 11 12 13 14 15  14 15 16 17 18 19 20
    19 20 21 22 23 24 25  16 17 18 19 20 21 22  21 22 23 24 25 26 27
    26 27 28 29 30 31     23 24 25 26 27 28 29  28 29 30 31
                          30

### Show some command periodically
    [marslo@MJ ~]
    $ whatch --interval 1 ls -alt

### Print 50th char
    [marslo@MJ ~]
    $ awk 'BEGIN{while (a++<50) s=s "-"; print s}'
    --------------------------------------------------

### Batch move
    [marslo@MJ ~]
    $ mkdir backup-folder && ls | grep -Ze ".*rar" | xargs -d '\n' -I {} mv {} backup-folder

### Show all line numbers in a file
    - Method 1
        <pre><code>[marslo@MJ ~]
        $ sudo cat /etc/passwd | wc -l
        36
        </code></pre>

    - Method 2
        <pre><code>[marslo@MJ ~]
        $ awk 'END {print NR}' /etc/passwd
        36
        </code></pre>

### Clear
    [marslo@MJ ~]
    $ printf "\ec"

### Encrypt bash file
    [marslo@MJ ~]
    $ echo "ls" > script.bash; gpg -c script.bash; cat script.bash.gpg | gpg -d --no-mdc-warning | bash

### Get URL
    [marslo@MJ ~]
    $ echo http://www.baidu.com | awk '{for(i=1;i<=NF;i++){if($i~/^(http|ftp):\/\//)print $i}}'http://www.baidu.com

### Get the count of a word in a file
    [marslo@MJ ~]
    $ cat /etc/passwd | grep marslo -o | wc -l
    3

    Or
    $ find . -name file.txt | xargs -e grep "token" -o | wc -l

### Download and unzip
    [marslo@MJ ~]
    $ wget -O - http://example.com/a.gz | tar xz

### Get the common part
    [marslo@MJ ~/GoodNote]
    $ cat a.txt
    1
    2
    3
    [marslo@MJ ~/GoodNote]
    $ cat b.txt
    3
    4
    5
    9
    [marslo@MJ ~/GoodNote]
    $ comm -12 a.txt b.txt > common
    [marslo@MJ ~/GoodNote]
    $ cat common
    3

### Revert a word
    [marslo@MJ ~/GoodNote]
    $ echo linux | rev
    xunil

### Use less as tail -f
    [marslo@MJ ~]
    $ less +F <filename>

### Print a file into one line
    [marslo@MJ ~/GoodNote]
    $ cat a
    1
    2
    3
    4
    5
    [marslo@MJ ~/GoodNote]
    $ echo $(cat a)
    1 2 3 4 5

### Rename
    [marslo@MJ ~/GoodNote]
    $ l
    total 4.0K
    -rw-r--r-- 1 marslo marslo 10 Feb 21 00:43 a.b
    [marslo@MJ ~/GoodNote]
    $ rename -v 's/\./_/g' *
    a.b renamed as a_b
    [marslo@MJ ~/GoodNote]
    $ l
    total 4.0K
    -rw-r--r-- 1 marslo marslo 10 Feb 21 00:43 a_b

### Get the file inode
    [marslo@MJ ~/GoodNote]
    $ l -i a_b
    10224132 -rw-r--r-- 1 marslo marslo 10 Feb 21 00:43 a_b

### Format a file to a table
    [marslo@MJ ~/GoodNote]
    $ cat a_b
    1:1
    2:2
    3:3
    [marslo@MJ ~/GoodNote]
    $ column -tns: a_b
    1  1
    2  2
    3  3

### Identity an image
    [marslo@MJ ~/Accessory/Images/WallPapers]
    $ identify arms009.jpg |grep -o "[[:digit:]]*x[[:digit:]]*" |tail -1
    1024x768

### Get cookie from firefox
    $ grep -oP '"url":"\K[^"]+' $(ls -t ~/.mozilla/firefox/*/sessionstore.js | sed q)

### Echo 256 colors
    [marslo@MJ ~/GoodNote]
    $ for i in {0..255}; do echo -e "\e[38;05;${i}m${i}"; done | column -c 80 -s ' '; echo -e "\e[m"

    OR
    [marslo@MJ ~/GoodNote]
    $ yes "$(seq 1 255)" | while read i; do printf "\x1b[48;5;${i}m\n"; sleep .01; done

### Directory diff
    diff --suppress-common-lines -y <(cd path_to_dir1; find .|sort) <(cd path_to_dir2; find .|sort)

### Show last n lines in a file
    [marslo@MJ ~]
    $ tail /etc/passwd -n 3
    saned:x:115:123::/home/saned:/bin/false
    marslo:x:1000:1000:Marslo,,,:/home/marslo:/bin/bash
    mysql:x:1001:1001::/home/mysql:/bin/sh
    [marslo@MJ ~]
    $ tail /etc/passwd -n 2
    marslo:x:1000:1000:Marslo,,,:/home/marslo:/bin/bash
    mysql:x:1001:1001::/home/mysql:/bin/sh

### Get 000 to 100
    [marslo@MJ ~]
    $ echo 00{1..9} 0{10..99} 100
    001 002 003 004 005 006 007 008 009 010 011 012 013 014 015 016 017 018 019 020 021 022 023 024 025 026 027 028 029 030 031 032 033 034 035 036 037 038 039 040 041 042 043 044 045 046 047 048 049 050 051 052 053 054 055 056 057 058 059 060 061 062 063 064 065 066 067 068 069 070 071 072 073 074 075 076 077 078 079 080 081 082 083 084 085 086 087 088 089 090 091 092 093 094 095 096 097 098 099 100

### Fast copy or moving or someting ([Detials](http://www.manpager.com/linux/man1/bash.1.html) -> Brace Expansion)
    - Usage 1:
        [marslo@MJ ~]
        $ ls | grep foo
        [marslo@MJ ~]
        $ touch foo{1,2,3}
        [marslo@MJ ~]
        $ ls | grep foo
        foo1
        foo2
        foo3


    - Usage 2
        [marslo@MJ ~]
        $ ls | grep foo
        [marslo@MJ ~]
        $ touch foo-{a..d}
        [marslo@MJ ~]
        $ ls | grep foo
        foo-a
        foo-b
        foo-c
        foo-d


    - Usage 3
        [marslo@MJ ~]
        $ ls foo-*
        foo-a  foo-b  foo-c  foo-d
        [marslo@MJ ~]
        $ mv foo-{a,}
        [marslo@MJ ~]
        $ ls foo-*
        foo-  foo-b  foo-c  foo-d


    - Usage 4
        [marslo@MJ ~]
        $ mkdir -p test/{a,b,c,d}
        [marslo@MJ ~]
        $ tree test/
        test/
        ├── a
        ├── b
        ├── c
        └── d

        4 directories, 0 files

### Searching for commands without knowing their exact names
    [marslo@MJ ~]
    $ apropos editor | head
    Git::SVN::Editor (3pm) - commit driver for "git svn set-tree" and dcommit
    INIFILE (1)          - OpenLink Virtuoso Opensource ini File Editor
    atobm (1)            - bitmap editor and converter utilities for the X Window System
    bitmap (1)           - bitmap editor and converter utilities for the X Window System
    bmtoa (1)            - bitmap editor and converter utilities for the X Window System
    ed (1)               - line-oriented text editor
    editor (1)           - Nano's ANOther editor, an enhanced free Pico clone
    editres (1)          - a dynamic resource editor for X Toolkit applications
    ex (1)               - Vi IMproved, a programmers text editor
    gedit (1)            - text editor for the GNOME Desktop

### PWD's secrets
    [marslo@MJ ~]
    $ l | grep bc
    lrwxrwxrwx 1 marslo marslo   37 Mar  4 00:25 bc -> /home/marslo/Tools/Git/BrowserConfig//
    [marslo@MJ ~]
    $ cd bc/
    [marslo@MJ ~/bc]
    $ pwd -L
    /home/marslo/bc
    [marslo@MJ ~/bc]
    $ pwd -P
    /home/marslo/Tools/Git/BrowserConfig

### Insert into the first line
    [marslo@MJ ~]
    $ cat demo.file
    abc
    efg
    [marslo@MJ ~]
    $ echo "first line" | cat - demo.file
    first line
    abc
    efg

### List the command beginning with
    ┌─ (marslo@i181-eng183 ~) ->
    └─ $ compgen -c "system-config-"
    system-config-authentication
    system-config-authentication
    system-config-date
    system-config-firewall
    system-config-firewall-tui
    system-config-kdump
    system-config-keyboard
    system-config-keyboard
    system-config-network
    system-config-network
    system-config-network-cmd
    system-config-network-cmd
    system-config-network-tui
    system-config-printer
    system-config-printer-applet
    system-config-services
    system-config-services
    system-config-users

