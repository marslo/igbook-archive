- Show Path:
    <pre><code>[marslo@MJ ~]
    $ echo src::${PATH} | awk 'BEGIN{pwd=ENVIRON["PWD"];RS=":";FS="\n"}!$1{$1=pwd}$1!~/^\//{$1=pwd"/"$1}{print $1}'
    /home/marslo/src
    /home/marslo
    /home/marslo/.vim/tools/bin
    /usr/local/mysql/bin
    /usr/local/bcompare/bin
    /usr/lib/lightdm/lightdm
    /usr/local/sbin
    /usr/local/bin
    /usr/sbin
    /usr/bin
    /sbin
    /bin
    /usr/games
    /usr/local/games</code></pre>
    OR
    <pre><code>[marslo@MJ ~/GoodNote]
    $ echo "${PATH//:/$'\n'}"
    </code></pre>

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

- Check CPU support 64 bit or not
    <pre><code>[marslo@MJ ~]
    $ sudo dmidecode --type=processor | grep -i -A 1 charac
        Characteristics:
                64-bit capable
    </code></pre>

- Show some command periodically
    <pre><code>whatch --interval 1 ls -alt </code></pre>

- Print 50th char
    <pre><code>[marslo@MJ ~]
    $ awk 'BEGIN{while (a++<50) s=s "-"; print s}'
    --------------------------------------------------
    </code></pre>

- Import data to SQL and print process
    <pre><code>(pv -n ~/database.sql | mysql -u root -pPASSWORD -D database_name) 2>&1 | zenity --width 550 --progress --auto-close --auto-kill --title "Im
    </code></pre>

- Print memory only
    <pre><code>[marslo@MJ ~]
    $ ps -o comm,%mem,args -u marslo | more
    COMMAND         %MEM COMMAND
    gnome-keyring-d  0.0 /usr/bin/gnome-keyring-daemon --daemonize --login
    init             0.0 init --user
    ssh-agent        0.0 ssh-agent
    dbus-daemon      0.0 dbus-daemon --fork --session --address=unix:abstract=/tmp/dbus-i5FUVjzADG
    upstart-event-b  0.0 upstart-event-bridge
    window-stack-br  0.0 /usr/lib/i386-linux-gnu/hud/window-stack-bridge
    upstart-dbus-br  0.0 upstart-dbus-bridge --daemon --session --user --bus-name session
    upstart-dbus-br  0.0 upstart-dbus-bridge --daemon --system --user --bus-name system
    upstart-file-br  0.0 upstart-file-bridge --daemon --user
    ibus-daemon      0.1 /usr/bin/ibus-daemon --daemonize --xim
    ....
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

- Quick create bak file
    <pre><code>[marslo@MJ ~]
    $ l *filename*
    -rw-r--r-- 1 marslo marslo 0 Feb 21 00:18 filename
    [marslo@MJ ~]
    $ cp filename{,.bak}
    [marslo@MJ ~]
    $ l *filename*
    -rw-r--r-- 1 marslo marslo 0 Feb 21 00:18 filename
    -rw-r--r-- 1 marslo marslo 0 Feb 21 00:18 filename.bak
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

- Press Any Key to Continue
    <pre><code>[marslo@MJ ~]
    $ read -sn 1 -p "Press any key to continue..." && echo "\n"
    Press any key to continue...\n
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

- Get the Computer Version
    <pre><code>[marslo@MJ ~/GoodNote]
    $ sudo dmidecode | grep -i prod
            Product Name: Vostro 5560
            Product Name: 04YDT0
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

- Simulate type mechine [Pretty Cool!!]
    <pre><code>[marslo@MJ ~]
    $ sudo apt-get intall pv
    [marslo@MJ ~]
    $ echo "Very very very very very long words" | pv -qL $[10+(-2 + RANDOM%5)]
    </code></pre>
    OR
    <pre><code>[marslo@MJ ~/GoodNote]
    $ sudo apt-get install randtype
    [marslo@MJ ~/GoodNote]
    $ echo "Very very very very very long words" | randtype -m 4
    </code></pre>

- Get how many days left this years
    <pre><code>[marslo@MJ ~/GoodNote]
    $ echo "There are $(($(date +%j -d"Dec 31, $(date +%Y)")-$(date +%j))) left in year $(date +%Y)."
    There are 323 left in year 2014.
    </code></pre>

- cat /etc/cpuinfo
    <pre><code>[marslo@MJ ~/GoodNote]
    $ lscpu
    Architecture:          i686
    CPU op-mode(s):        32-bit, 64-bit
    Byte Order:            Little Endian
    CPU(s):                4
    On-line CPU(s) list:   0-3
    ....
    </code></pre>

- Get PATH line by line
    <pre><code>[marslo@MJ ~]
    $ echo src::${PATH} | awk 'BEGIN{pwd=ENVIRON["PWD"];RS=":";FS="\n"}!$1{$1=pwd}$1!~/^\//{$1=pwd"/"$1}{print $1}'
    /home/marslo/src
    /home/marslo
    /home/marslo/.vim/tools/bin
    /usr/local/mysql/bin
    /usr/local/bcompare/bin
    /usr/lib/lightdm/lightdm
    /usr/local/sbin
    /usr/local/bin
    /usr/sbin
    /usr/bin
    /sbin
    /bin
    /usr/games
    /usr/local/games
    </code></pre>

- cat
    <pre><code>[marslo@MJ ~/GoodNote]
    $ cat a_b
    1
    2
    3
    [marslo@MJ ~/GoodNote]
    $ tac a_b
    3
    2
    1
    </code></pre>

- Echo 256 colors
    <pre><code>[marslo@MJ ~/GoodNote]
    $ for i in {0..255}; do echo -e "\e[38;05;${i}m${i}"; done | column -c 80 -s ' '; echo -e "\e[m"
    </code></pre>
    OR
    <pre><code>[marslo@MJ ~/GoodNote]
    $ yes "$(seq 1 255)" | while read i; do printf "\x1b[48;5;${i}m\n"; sleep .01; done
    </code></pre>

- I'm very busy
    <pre><code>[marslo@MJ ~/GoodNote]
    $ cat /dev/urandom | hexdump -C | grep "ca fe"
    </code></pre>

- Directory diff
    <pre><code>diff --suppress-common-lines -y <(cd path_to_dir1; find .|sort) <(cd path_to_dir2; find .|sort)</code></pre>

- Clear duplicated PATH
    <pre><code>[marslo@MJ ~/GoodNote]
    $ export PATH=`echo -n $PATH | awk -v RS=":" '{ if (!x[$0]++) {printf s $0; s=":"} }'`
    </code></pre>

- Get week number
    <pre><code>[marslo@MJ ~/GoodNote]
    $ date +"%V"
    08
    </code></pre>

- DOS tree
    <pre><code>[marslo@MJ ~/GoodNote]
    $ find . -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'
    .
    |____a_b
    |____b_a
    </code></pre>

- Set Volume by command
    <pre><code>[marslo@MJ ~/GoodNote]
    $ pacmd set-sink-volume 0 0x10000
    Welcome to PulseAudio! Use "help" for usage information.
    </code></pre>
-

