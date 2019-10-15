<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Install MySQL from Source code](#install-mysql-from-source-code)
- [Make mysql as boot start](#make-mysql-as-boot-start)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Install MySQL from Source code
### Usefull Links
- Community Server
    - [5.7 MySQL Community Server](http://dev.mysql.com/downloads/mysql/)
    - [5.6 MySQL Community Server](http://dev.mysql.com/downloads/mysql/5.6.html)
- MySQL source code
    - [mysql-5.7.3-m13.tar.gz](http://cdn.mysql.com/Downloads/MySQL-5.7/mysql-5.7.3-m13.tar.gz)
    - [mysql-5.6.16.tar.gz](http://dev.mysql.com/get/Downloads/MySQL-5.6/mysql-5.6.16.tar.gz)
- Documents
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

##### [Log of mysql_install_db --user=mysql](https://github.com/Marslo/MyNotes/blob/master/MySQL/mysql_install_db.md)

#### Change Permission again

    # chown -R root .
    # chown -R mysql data

#### Start mysqld_safe

    # bin/mysqld_safe --user=mysql &

#### Setup root password

    # ./bin/mysqladmin -u root password '<PASSWORDHERE>'
Or

    # ./bin/mysql_secure_installation

##### [Log of mysql_secure_installatioin](https://github.com/Marslo/MyNotes/blob/master/MySQL/mysql_secure_installation.md)

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
