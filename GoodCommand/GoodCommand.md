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
