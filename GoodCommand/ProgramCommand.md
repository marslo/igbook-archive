### Import data to SQL and print process
    (pv -n ~/database.sql | mysql -u root -pPASSWORD -D database_name) 2>&1 | zenity --width 550 --progress --auto-close --auto-kill --title "Im

### Get the cnf file location for MySQL
    [marslo@MJ ~]
    $ mysql - ? | grep ".cnf" -C 1
    Default options are read from the following files in the given order:
    /etc/my.cnf /etc/mysql/my.cnf /usr/local/mysql/etc/my.cnf ~/.my.cnf
    The following groups are read: mysql client

### Get the git change from .git/objects
    [marslo@MJ ~]
    $ find .git/objects -type f -printf "%P\n" | sed s,/,, | while read object; do echo "=== $obj $(git cat-file -t $object) ==="; git cat-file -p $object; done
