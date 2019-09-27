<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [SSH Tricky](#ssh-tricky)
  - [Generate SSH Key](#generate-ssh-key)
  - [Add into agent](#add-into-agent)
  - [Performance](#performance)
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
## Generate SSH Key

```bash
$ keyname='marslo@china'
# rsa4096
$ ssh-keygen -t rsa -b 4096 -f "~/.ssh/${keyname}" -C "${keyname}" -P "" -q

# ed25519
$ ssh-keygen -t ed25519 -o -a 100 -C "${keyname}" -f "~/.ssh/${keyname}" -P '' -q
```

## Add into agent

```bash
$ ssh-add ~/.ssh/${keyname}

# e.g.:
$ ssh-add ~/.ssh/id_ed25519 
Identity added: /Users/marslo/.ssh/id_ed25519 (marslo@devops)

$ ssh-agent -s
SSH_AUTH_SOCK=/var/folders/s3/mg_f3cv54nn7y758j_t46zt40000gn/T//ssh-MgCrKA3ZS06N/agent.25376; export SSH_AUTH_SOCK;
SSH_AGENT_PID=25377; export SSH_AGENT_PID;
echo Agent pid 25377;
```

## Performance

```bash
$ openssl speed rsa1024 rsa2048 dsa1024 dsa2048
Doing 1024 bit private rsa's for 10s: 91211 1024 bit private RSA's in 9.97s
Doing 1024 bit public rsa's for 10s: 1161461 1024 bit public RSA's in 9.93s
Doing 2048 bit private rsa's for 10s: 12305 2048 bit private RSA's in 9.94s
Doing 2048 bit public rsa's for 10s: 403455 2048 bit public RSA's in 9.98s
Doing 1024 bit sign dsa's for 10s: 84873 1024 bit DSA signs in 10.00s
Doing 1024 bit verify dsa's for 10s: 109544 1024 bit DSA verify in 9.99s
Doing 2048 bit sign dsa's for 10s: 30010 2048 bit DSA signs in 9.99s
Doing 2048 bit verify dsa's for 10s: 33202 2048 bit DSA verify in 9.98s
OpenSSL 1.0.2t  10 Sep 2019
built on: reproducible build, date unspecified
options:bn(64,64) rc4(ptr,int) des(idx,cisc,16,int) aes(partial) idea(int) blowfish(idx) 
compiler: clang -I. -I.. -I../include  -fPIC -fno-common -DOPENSSL_PIC -DOPENSSL_THREADS -D_REENTRANT -DDSO_DLFCN -DHAVE_DLFCN_H -arch x86_64 -O3 -DL_ENDIAN -Wall -DOPENSSL_IA32_SSE2 -DOPENSSL_BN_ASM_MONT -DOPENSSL_BN_ASM_MONT5 -DOPENSSL_BN_ASM_GF2m -DSHA1_ASM -DSHA256_ASM -DSHA512_ASM -DMD5_ASM -DAES_ASM -DVPAES_ASM -DBSAES_ASM -DWHIRLPOOL_ASM -DGHASH_ASM -DECP_NISTZ256_ASM
                  sign    verify    sign/s verify/s
rsa 1024 bits 0.000109s 0.000009s   9148.5 116964.9
rsa 2048 bits 0.000808s 0.000025s   1237.9  40426.4
                  sign    verify    sign/s verify/s
dsa 1024 bits 0.000118s 0.000091s   8487.3  10965.4
dsa 2048 bits 0.000333s 0.000301s   3004.0   3326.9
```

## Get Public Key from Private Key

```bash
$ ssh-keygen -y -f ~/.ssh/id_rsa > ~/.ssh/id_rsa.pub
```

## Disable Login Password

```bash
$ cat /etc/ssh/sshd_config
ChallengeResponseAuthentication no
PasswordAuthentication no
UsePAM no
```

## Force Use Password

```bash
$ ssh -o PreferredAuthentications=password -o PubkeyAuthentication=no user@target.server
```

## Get FingerPrinter from Private Key
* SHA256:

```bash
$ ssh-keygen -l -f ~/.ssh/id_rsa
# or
$ ssh-keygen -l -f ~/.ssh/id_rsa.pub
```

* MD5:

```bash
$ ssh-keygen -E md5 -l -f ~/.ssh/id_rsa
# OR
$ ssh-keygen -E md5 -l -f ~/.ssh/id_rsa.pub
```

## SSH with OpenSSL

```bash
$ openssl pkey -in ~/.ssh/ec2/primary.pem -pubout -outform DER | openssl md5 -c
```

# SSH With Proxy
## Using Command Directly
* Linux:

```bash
$ ssh -o 'ProxyCommand nc -x proxy.url.com proxy-port %h %p' -vT user@target.server
# or
$ ssh -o 'ProxyCommand corkscrew proxy.url.com proxy-port %h %p' -vT user@target.server
```

* Windows:
    * Git for Windows

    ```bash
    $ ssh -o 'ProxyCommand connect -H http://proxy.url.com:proxy-port %h %p' user@target.server
    ```

    * Cygwin

    ```bash
    $ apt-cyg install corkscrew
    $ ssh -o 'ProxyCommand corkscrew proxy.url.com proxy-port %h %p' user@target.server
    ```

    OR

    ```bash
    $ apt-cyg install nc
    $ ssh -o 'ProxyCommand nc -X connect -x proxy.url.com:proxy-port %h %p' -vT git@github.com
    ```

## Using Configure file
```bash
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
```
OR

```bash
$ cat ~/.ssh/config
HOST  *
      GSSAPIAuthentication no
      StrictHostKeyChecking no
      # UserKnownHostsFile /dev/null

Host  github.com
      Hostname              github.com
      User                  marslo.jiao@gmail.com
      IdentityFile          /C/Marslo/my@key
      ProxyCommand          nc -X connect -x proxy.url.com:proxy-port %h %p
      IdentitiesOnly        yes
      ServerAliveInterval   10                      # Optional
```

## Reference
- [透过代理连接SSH](http://blog.csdn.net/asx20042005/article/details/7041294)
- [SSH ProxyCommand example: Going through one host to reach another server](https://www.cyberciti.biz/faq/linux-unix-ssh-proxycommand-passing-through-one-host-gateway-server/)
- [OpenSSH/Cookbook/Proxies and Jump Hosts](https://en.wikibooks.org/wiki/OpenSSH/Cookbook/Proxies_and_Jump_Hosts#ProxyCommand_with_Netcat)
- [Tunneling SSH over PageKite](https://pagekite.net/wiki/Howto/SshOverPageKite/#wrongnetcat)
- [Transparent Multi-hop SSH](http://sshmenu.sourceforge.net/articles/transparent-mulithop.html)
- [SSH via HTTP proxy in OSX](http://www.perkin.org.uk/posts/ssh-via-http-proxy-in-osx.html)
