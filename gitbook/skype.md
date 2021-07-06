# skype

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [Install skype in Ubuntu 64bit](skype.md#install-skype-in-ubuntu-64bit)

## Install skype in Ubuntu 64bit

* Inspired from [AskUbuntu](http://askubuntu.com/questions/215298/unable-to-install-skype-on-64bit-ubuntu)
* Add i386 architecture

  ```bash
    $ sudo dpkg --add-architecture i386
    $ sudo apt-get update
  ```

* Add Repo and install by `apt-get`

  ```bash
    $ sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
    $ sudo apt-get update && sudo apt-get install skype
  ```

  OR

* Add by `dpkg`

  ```bash
    $ wget http://www.skype.com/go/getskype-linux-ubuntu-64/skype-ubuntu-quantal_4.1.0.20-1_amd64.deb
    $ sudo dpkg -i skype-ubuntu*.deb
  ```

