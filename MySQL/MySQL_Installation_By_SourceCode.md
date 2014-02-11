## Install MySQL from Source code

### Usefull Links
- [MySQL Community Server](http://dev.mysql.com/downloads/mysql/)
- [mysql-5.7.3-m13.tar.gz](http://cdn.mysql.com/Downloads/MySQL-5.7/mysql-5.7.3-m13.tar.gz)
- [MySQL Document](http://dev.mysql.com/doc/)
- [MySQL Online manual](http://dev.mysql.com/doc/refman/5.7/en/)
- [2.8.2. Installing MySQL Using a Standard Source Distribution](http://dev.mysql.com/doc/refman/5.7/en/installing-source-distribution.html)
- [2.8.4. MySQL Source-Configuration Options](http://dev.mysql.com/doc/refman/5.7/en/source-configuration-options.html)

### Preconfiguration Setup
#### Create user and group

    # groupadd mysql
    # useradd -r -g mysql mysql

#### Extract tar.gz

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

#### Permission Manager

    # chown -R mysql:mysql /usr/local/mysql

#### Initinal MySQL

    # scripts/mysql_install_db --user=mysql
    # cp support-files/mysql.server /etc/init.d/mysqld

#### Change Permission again

    # chown -R root .
    # chown -R mysql data

#### Start mysqld_safe

    # bin/mysqld_safe --user=mysql &

#### Setup root password

    # ./bin/mysqladmin -u root password 'root'
Or

    # ./bin/mysql_secure_installation

#### Set Environment

    # cat >> /etc/bash.bashrc << EOF
    > export PATH=/usr/local/mysql/bin:$PATH
    > EOF

##### [cmake logs](https://github.com/Marslo/MyNotes/blob/master/MySQL/MySQL_Cmake_Logs.md)
