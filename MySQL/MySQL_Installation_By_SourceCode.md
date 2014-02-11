## Install MySQL from Source code
### Contact
- [Usefull Links](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#usefull-links)
- [Compile and Install](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#compile-and-install)
    - [Preconfiguratio setup](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#preconfiguration-setup)
        - [Create user and group account](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#create-user-and-group)
        - [Extract tar.gz](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#extract-targz)
    - [Compile and install](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#compile-and-install)
- [Configuration and Initial](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#configuration-and-initial)
    - [Change permission](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#permission-manager)
    - [Initial Mysql](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#initial-mysql)
    - [Change Permission again](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#change-permission-again)
    - [Start mysqld_safe](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#start-mysqld_safe)
    - [Setup root password](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#setup-root-password)
- [Set Envionment](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#set-environment)
- [Check the mysql port](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#check-the-mysql-port)
-[Check variables](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#check-variables)
- [Make msyql as boot start](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Installation_By_SourceCode.md#make-mysql-as-boot-start)

### Usefull Links
- [MySQL Community Server](http://dev.mysql.com/downloads/mysql/)
- [mysql-5.7.3-m13.tar.gz](http://cdn.mysql.com/Downloads/MySQL-5.7/mysql-5.7.3-m13.tar.gz)
- [MySQL Document](http://dev.mysql.com/doc/)
- [MySQL Online manual](http://dev.mysql.com/doc/refman/5.7/en/)
- [2.8.2. Installing MySQL Using a Standard Source Distribution](http://dev.mysql.com/doc/refman/5.7/en/installing-source-distribution.html)
- [2.8.4. MySQL Source-Configuration Options](http://dev.mysql.com/doc/refman/5.7/en/source-configuration-options.html)

### Compile and Install
#### Preconfiguration Setup
##### Create user and group

    # groupadd mysql
    # useradd -r -g mysql mysql

##### Extract tar.gz

    # tar xf mysql-5.7.3-m13.tar.gz
    # cd mysql-5.7.3-m13

#### Compile and Install

    # cmake . -DCMAKE_INSTALL_PREFIX=/usr/local/mysql \
    > -DDEFAULT_CHARSET=gbk \
    > -DDEFAULT_COLLATION=gbk_chinese_ci \
    > -DENABLED_LOCAL_INFILE=ON \
    > -DWITH_INNOBASE_STORAGE_ENGINE=1 \
    > -DWITH_FEDERATED_STORAGE_ENGINE=1 \
    > -DWITH_BLACKHOLE_STORAGE_ENGINE=1 \
    > -DMYSQL_UNIX_ADDR=/tmp/mysqld.sock \
    > -DWITH_DEBUG=0 \
    > -DMYSQL_TCP_PORT=3306
    # make
    # make install

##### [cmake logs](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Cmake_Logs.md)

### Configuration and Initial
#### Permission Manager

    # chown -R mysql:mysql /usr/local/mysql

#### Initial MySQL

    # scripts/mysql_install_db --user=mysql
    # cp support-files/mysql.server /etc/init.d/mysqld

#### [Log of mysql_install_db --user=mysql](https://github.com/Marslo/MyNotes/blob/master/MySQL/mysql_install_db.md)

#### Change Permission again

    # chown -R root .
    # chown -R mysql data

#### Start mysqld_safe

    # bin/mysqld_safe --user=mysql &

#### Setup root password

    # ./bin/mysqladmin -u root password '<PASSWORDHERE>'
Or

    # ./bin/mysql_secure_installation

#### [Log of mysql_secure_installatioin](https://github.com/Marslo/MyNotes/blob/master/MySQL/mysql_secure_installation.md)

### Set Environment

    # cat >> /etc/bash.bashrc << EOF
    > export PATH=/usr/local/mysql/bin:$PATH
    > EOF

### Check the mysql port

    sudo netstat -tunlp  | grep 3306
    tcp6       0      0 :::3306                 :::*                    LISTEN      21712/mysqld

### Check variables

    # mysqladmin variables -p
    Enter password:

## Make mysql as boot start

    chkconfig --add mysqld
    chkconfig --level 345 mysqld on
