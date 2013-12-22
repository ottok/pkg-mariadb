TokuDB
======

TokuDB is a high-performance, transactional storage engine for MySQL and
MariaDB.  For more details, see our [product page][products].

This repository contains the MySQL plugin that uses the [TokuKV][tokukv]
core.

There are also patches to the MySQL and MariaDB kernels, available in our
forks of [mysql][mysql] and [mariadb][mariadb].

[products]: http://www.tokutek.com/products/tokudb-for-mysql/
[tokukv]: http://github.com/Tokutek/ft-index
[mysql]: http://github.com/Tokutek/mysql
[mariadb]: http://github.com/Tokutek/mariadb


Building
--------

The `scripts/` directory contains a script that can be used to build a
working MySQL or MariaDB with Tokutek patches, and with the TokuDB storage
engine, called `make.mysql.bash`.  This script will download copies of the
needed source code from github and build everything.

To build MySQL with TokuDB 7.0.4:
```sh
scripts/make.mysql.bash --mysqlbuild=mysql-5.5.30-tokudb-7.0.4-linux-x86_64
```

To build MariaDB with TokuDB 7.0.4:
```sh
scripts/make.mysql.bash --mysqlbuild=mariadb-5.5.30-tokudb-7.0.4-linux-x86_64
```

Before you start, make sure you have a C++11-compatible compiler (GCC >=
4.7 is recommended), as well as CMake >=2.8.8, and the libraries and
header files for valgrind,zlib, and Berkeley DB.  On Centos, `yum install
valgrind-devel zlib-devel libdb-devel`, on Ubuntu, `apt-get install
valgrind zlib1g-dev libdb-dev`.

You can set the compiler by passing `--cc` and `--cxx` to the script, to
select one that's new enough.  The default is `scripts/make.mysql.bash
--cc=gcc47 --cxx=g++47`, which may not exist on your system.


Contributing
------------

Please report bugs in TokuDB here on github.

We have two publicly accessible mailing lists:

 - tokudb-user@googlegroups.com is for general and support related
   questions about the use of TokuDB.
 - tokudb-dev@googlegroups.com is for discussion of the development of
   TokuDB.

We are also available on IRC on freenode.net, in the #tokutek channel.


License
-------

TokuDB is available under the GPL version 2.  See [COPYING][copying]

The TokuKV component of TokuDB is available under the GPL version 2, with
slight modifications.  See [README-TOKUDB][license].

[copying]: http://github.com/Tokutek/ft-engine/blob/master/COPYING
[license]: http://github.com/Tokutek/ft-index/blob/master/README-TOKUDB
