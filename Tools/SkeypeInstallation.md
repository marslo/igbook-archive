<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Install skype in Ubuntu 64bit](#install-skype-in-ubuntu-64bit)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

### Install skype in Ubuntu 64bit
- Inspired from [AskUbuntu](http://askubuntu.com/questions/215298/unable-to-install-skype-on-64bit-ubuntu)
- Add i386 architecture
    <pre><code>┌─ (marslo@MarsloJiao ~) ->
    └─ $ sudo dpkg --add-architecture i386
    ┌─ (marslo@MarsloJiao ~) ->
    └─ $ sudo apt-get update
    </code></pre>
- Add Repo and install by `apt-get`
    <pre><code>┌─ (marslo@MarsloJiao ~) ->
    └─ $ sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
    ┌─ (marslo@MarsloJiao ~) ->
    └─ $ sudo apt-get update && sudo apt-get install skype
    </code></pre>
OR
- Add by `dpkg`
    <pre><code>┌─ (marslo@MarsloJiao ~) ->
    └─ $ wget http://www.skype.com/go/getskype-linux-ubuntu-64/skype-ubuntu-quantal_4.1.0.20-1_amd64.deb
    ┌─ (marslo@MarsloJiao ~) ->
    └─ $ sudo dpkg -i skype-ubuntu*.deb
    </code></pre>
