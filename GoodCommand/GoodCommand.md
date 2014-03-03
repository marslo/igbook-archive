- Show Cal
    <pre><code>marslo@MJ ~]
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
    </code></pre>


- Show some command periodically
    <pre><code>whatch --interval 1 ls -alt </code></pre>

- Print 50th char
    <pre><code>[marslo@MJ ~]
    $ awk 'BEGIN{while (a++<50) s=s "-"; print s}'
    --------------------------------------------------
    </code></pre>

- Batch move
    <pre><code>[marslo@MJ ~]
    $ mkdir backup-folder && ls | grep -Ze ".*rar" | xargs -d '\n' -I {} mv {} backup-folder
    </code></pre>

- Show all line numbers in a file
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

- Clear
    <pre><code>[marslo@MJ ~]
    $ printf "\ec"
    </code></pre>

- Encrypt bash file
    <pre><code>[marslo@MJ ~]
    $ echo "ls" > script.bash; gpg -c script.bash; cat script.bash.gpg | gpg -d --no-mdc-warning | bash
    </code></pre>

- Get URL
    <pre><code>[marslo@MJ ~]
    $ echo http://www.baidu.com | awk '{for(i=1;i<=NF;i++){if($i~/^(http|ftp):\/\//)print $i}}'http://www.baidu.com
    </code></pre>

- Get the count of a word in a file
    <pre><code>[marslo@MJ ~]
    $ cat /etc/passwd | grep marslo -o | wc -l
    3
    </code></pre>
    Or
    <pre><code>$ find . -name file.txt | xargs -e grep "token" -o | wc -l
    </code></pre>


- Download and unzip
    <pre><code>[marslo@MJ ~]
    $ wget -O - http://example.com/a.gz | tar xz
    </code></pre>

- Get the common part
    <pre><code>[marslo@MJ ~/GoodNote]
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
    </code></pre>

- Revert a word
    <pre><code>[marslo@MJ ~/GoodNote]
    $ echo linux | rev
    xunil
    </code></pre>

- Use less as tail -f
    <pre><code>[marslo@MJ ~]
    $ less +F <filename>
    </code></pre>

- Print a file into one line
    <pre><code>[marslo@MJ ~/GoodNote]
    $ cat a
    1
    2
    3
    4
    5
    [marslo@MJ ~/GoodNote]
    $ echo $(cat a)
    1 2 3 4 5
    </code></pre>

- Rename
    <pre><code>[marslo@MJ ~/GoodNote]
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
    </code></pre>

- Get the file inode
    <pre><code>[marslo@MJ ~/GoodNote]
    $ l -i a_b
    10224132 -rw-r--r-- 1 marslo marslo 10 Feb 21 00:43 a_b
    </code></pre>

- Format a file to a table
    <pre><code>[marslo@MJ ~/GoodNote]
    $ cat a_b
    1:1
    2:2
    3:3
    [marslo@MJ ~/GoodNote]
    $ column -tns: a_b
    1  1
    2  2
    3  3
    </code></pre>

- Identity an image
    <pre><code>[marslo@MJ ~/Accessory/Images/WallPapers]
    $ identify arms009.jpg |grep -o "[[:digit:]]*x[[:digit:]]*" |tail -1
    1024x768
    </code></pre>

- Get cookie from firefox
    <pre><code>
    $ grep -oP '"url":"\K[^"]+' $(ls -t ~/.mozilla/firefox/*/sessionstore.js | sed q)
    </code></pre>

- Echo 256 colors
    <pre><code>[marslo@MJ ~/GoodNote]
    $ for i in {0..255}; do echo -e "\e[38;05;${i}m${i}"; done | column -c 80 -s ' '; echo -e "\e[m"
    </code></pre>
    OR
    <pre><code>[marslo@MJ ~/GoodNote]
    $ yes "$(seq 1 255)" | while read i; do printf "\x1b[48;5;${i}m\n"; sleep .01; done
    </code></pre>

- Directory diff
    <pre><code>diff --suppress-common-lines -y <(cd path_to_dir1; find .|sort) <(cd path_to_dir2; find .|sort)</code></pre>

- Show last n lines in a file
    <pre><code>[marslo@MJ ~]
    $ tail /etc/passwd -n 3
    saned:x:115:123::/home/saned:/bin/false
    marslo:x:1000:1000:Marslo,,,:/home/marslo:/bin/bash
    mysql:x:1001:1001::/home/mysql:/bin/sh
    [marslo@MJ ~]
    $ tail /etc/passwd -n 2
    marslo:x:1000:1000:Marslo,,,:/home/marslo:/bin/bash
    mysql:x:1001:1001::/home/mysql:/bin/sh
    </code></pre>

- Get 000 to 100
    <pre><code>[marslo@MJ ~]
    $ echo 00{1..9} 0{10..99} 100
    001 002 003 004 005 006 007 008 009 010 011 012 013 014 015 016 017 018 019 020 021 022 023 024 025 026 027 028 029 030 031 032 033 034 035 036 037 038 039 040 041 042 043 044 045 046 047 048 049 050 051 052 053 054 055 056 057 058 059 060 061 062 063 064 065 066 067 068 069 070 071 072 073 074 075 076 077 078 079 080 081 082 083 084 085 086 087 088 089 090 091 092 093 094 095 096 097 098 099 100
    </code></pre>

- Fast copy or moving or someting ([Detials](http://www.manpager.com/linux/man1/bash.1.html) -> Brace Expansion)
    - Usage 1:
        <pre><code>[marslo@MJ ~]
        $ ls | grep foo
        [marslo@MJ ~]
        $ touch foo{1,2,3}
        [marslo@MJ ~]
        $ ls | grep foo
        foo1
        foo2
        foo3
        </code></pre>

    - Usage 2
        <pre><code>[marslo@MJ ~]
        $ ls | grep foo
        [marslo@MJ ~]
        $ touch foo-{a..d}
        [marslo@MJ ~]
        $ ls | grep foo
        foo-a
        foo-b
        foo-c
        foo-d
        </code></pre>

    - Usage 3
        <pre><code>[marslo@MJ ~]
        $ ls foo-*
        foo-a  foo-b  foo-c  foo-d
        [marslo@MJ ~]
        $ mv foo-{a,}
        [marslo@MJ ~]
        $ ls foo-*
        foo-  foo-b  foo-c  foo-d
        </code></pre>

    - Usage 4
        <pre><code>[marslo@MJ ~]
        $ mkdir -p test/{a,b,c,d}
        [marslo@MJ ~]
        $ tree test/
        test/
        ├── a
        ├── b
        ├── c
        └── d

        4 directories, 0 files
        </code></per>
