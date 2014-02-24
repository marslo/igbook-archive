- Import data to SQL and print process
    <pre><code>(pv -n ~/database.sql | mysql -u root -pPASSWORD -D database_name) 2>&1 | zenity --width 550 --progress --auto-close --auto-kill --title "Im
    </code></pre>

- Get the cnf file location for MySQL
    <pre><code>[marslo@MJ ~]
    $ mysql - ? | grep ".cnf" -C 1
    Default options are read from the following files in the given order:
    /etc/my.cnf /etc/mysql/my.cnf /usr/local/mysql/etc/my.cnf ~/.my.cnf 
    The following groups are read: mysql client
    </code></pre>

- Get the git change from .git/objects
    <pre><code>[marslo@MJ ~]
    $ find .git/objects -type f -printf "%P\n" | sed s,/,, | while read object; do echo "=== $obj $(git cat-file -t $object) ==="; git cat-file -p $object; done
    </code></pre>
