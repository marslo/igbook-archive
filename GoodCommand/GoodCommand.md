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

- Show Cal
    <pre><code>marslo@MJ ~/Tools/Git/MyNotes]
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
