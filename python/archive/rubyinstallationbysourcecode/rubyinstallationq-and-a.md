# rubyInstallationQ&A

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [openssl.h](rubyinstallationq-and-a.md#opensslh)
* [thread\_native.h](rubyinstallationq-and-a.md#thread_nativeh)
* [sqlite3.h](rubyinstallationq-and-a.md#sqlite3h)
* [libyaml-0.so.2 & psych.so](rubyinstallationq-and-a.md#libyaml-0so2--psychso)

## openssl.h

* Error Description

  ```text
  ┌─ (marslo@MarsloJiao ~/Tools/SourceCode/Ruby/ruby-2.1.2/ext/openssl) ->
    └─ $ ruby extconf.rb
    ...
    checking for openssl/ssl.h... no
    ...
  ```

* Solution

    [Install openssl lib](https://github.com/Marslo/MyBlog/blob/master/GoodCommand/CompileQ&A.md#sslh)

  ```text
  ┌─ (marslo@MarsloJiao ~/Tools/SourceCode/Ruby/ruby-2.1.2/ext/openssl) ->
    └─ $ sudo apt-get intall libssl-dev
    ┌─ (marslo@MarsloJiao ~) ->
    └─ $ dpkg -l | grep openssl
    ii  libcurl3:amd64                      7.35.0-1ubuntu2                            amd64        easy-to-use client-side URL transfer library (OpenSSL flavour)
    ii  libcurl4-openssl-dev:amd64          7.35.0-1ubuntu2                            amd64        development files and documentation for libcurl (OpenSSL flavour)
    ii  libgnutls-openssl27:amd64           2.12.23-12ubuntu2.1                        amd64        GNU TLS library - OpenSSL wrapper
    ii  openssl                             1.0.1f-1ubuntu2.4                          amd64        Secure Sockets Layer toolkit - cryptographic utility
    ii  python-openssl                      0.13-2ubuntu6                              amd64        Python 2 wrapper around the OpenSSL library
  ```

## thread\_native.h

* Error Description 
* Solution Add `top_srcdir=../..` into Makefile \(the 63th line as below\) 

## sqlite3.h

* Error Description 
* Solution Install `libsqlite3-dev` in Ubuntu as the error logged 

## libyaml-0.so.2 & psych.so

* Error Description 
* Solution 

