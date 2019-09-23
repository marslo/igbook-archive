<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

    - [Content](#content)
- [SSH Tricky](#ssh-tricky)
    - [Get Public Key from Private Key](#get-public-key-from-private-key)
    - [Disable Login Password](#disable-login-password)
    - [Force Use Password](#force-use-password)
    - [Get FingerPrinter from Private Key](#get-fingerprinter-from-private-key)
    - [SSH with OpenSSL](#ssh-with-openssl)
- [SSH With Proxy](#ssh-with-proxy)
    - [Using Command Directly](#using-command-directly)
    - [Using Configure file](#using-configure-file)
    - [Reference](#reference)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Content
- [SSH Tricky](#ssh-tricky)
- [SSH With Proxy](#ssh-with-proxy)


# SSH Tricky
## Get Public Key from Private Key

    $ ssh-keygen -y -f ~/.ssh/id_rsa > ~/.ssh/id_rsa.pub

## Disable Login Password

    $ cat /etc/ssh/sshd_config
    ChallengeResponseAuthentication no
    PasswordAuthentication no
    UsePAM no

## Force Use Password

    $ ssh -o PreferredAuthentications=password -o PubkeyAuthentication=no user@target.server

## Get FingerPrinter from Private Key
* SHA256:

        $ ssh-keygen -l -f ~/.ssh/id_rsa
        OR
        $ ssh-keygen -l -f ~/.ssh/id_rsa.pub
* MD5:

        $ ssh-keygen -E md5 -l -f ~/.ssh/id_rsa
        OR
        $ ssh-keygen -E md5 -l -f ~/.ssh/id_rsa.pub

## SSH with OpenSSL

    $ openssl pkey -in ~/.ssh/ec2/primary.pem -pubout -outform DER | openssl md5 -c

# SSH With Proxy
## Using Command Directly
* Linux:

        $ ssh -o 'ProxyCommand nc -x proxy.url.com proxy-port %h %p' -vT user@target.server
        OR
        $ ssh -o 'ProxyCommand corkscrew proxy.url.com proxy-port %h %p' -vT user@target.server

* Windows:
    * Git for Windows

            $ ssh -o 'ProxyCommand      connect -H http://proxy.url.com:proxy-port %h %p' user@target.server
    * Cygwin
            $ apt-cyg install corkscrew
            $ ssh -o 'ProxyCommand corkscrew proxy.url.com proxy-port %h %p' user@target.server

    OR

            $ apt-cyg install nc
            $ ssh -o 'ProxyCommand nc -X connect -x proxy.url.com:proxy-port %h %p' -vT git@github.com

## Using Configure file

    $ cat ~/.ssh/config
    HOST  *
          GSSAPIAuthentication no
          StrictHostKeyChecking no
          # UserKnownHostsFile /dev/null

    Host  github.com
          Hostname          github.com
          User              marslo.jiao@gmail.com
          IdentityFile      /C/Marslo/my@key
          ProxyCommand      connect -H http://185.46.212.34:10015 %h %p
          IdentitiesOnly    yes

OR

    $ cat ~/.ssh/config
    HOST  *
          GSSAPIAuthentication no
          StrictHostKeyChecking no
          # UserKnownHostsFile /dev/null

    Host  github.com
          Hostname          github.com
          User              marslo.jiao@gmail.com
          IdentityFile      /C/Marslo/my@key
          ProxyCommand      nc -X connect -x proxy.url.com:proxy-port %h %p
          IdentitiesOnly    yes
          ServerAliveInterval   10                      # Optional


## Reference
- [透过代理连接SSH](http://blog.csdn.net/asx20042005/article/details/7041294)
- [SSH ProxyCommand example: Going through one host to reach another server](https://www.cyberciti.biz/faq/linux-unix-ssh-proxycommand-passing-through-one-host-gateway-server/)
- [OpenSSH/Cookbook/Proxies and Jump Hosts](https://en.wikibooks.org/wiki/OpenSSH/Cookbook/Proxies_and_Jump_Hosts#ProxyCommand_with_Netcat)
- [Tunneling SSH over PageKite](https://pagekite.net/wiki/Howto/SshOverPageKite/#wrongnetcat)
- [Transparent Multi-hop SSH](http://sshmenu.sourceforge.net/articles/transparent-mulithop.html)
- [SSH via HTTP proxy in OSX](http://www.perkin.org.uk/posts/ssh-via-http-proxy-in-osx.html)
