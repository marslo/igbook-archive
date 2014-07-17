### openssl.h
- Error Description
    <pre><code>┌─ (marslo@MarsloJiao ~/Tools/SourceCode/Ruby/ruby-2.1.2/ext/openssl) ->
    └─ $ ruby extconf.rb
    ...
    checking for openssl/ssl.h... no
    ...
    </code></pre>
- Solution
    [Install openssl lib](https://github.com/Marslo/MyBlog/blob/master/GoodCommand/CompileQ&A.md#sslh)
    <pre><code>┌─ (marslo@MarsloJiao ~/Tools/SourceCode/Ruby/ruby-2.1.2/ext/openssl) ->
    └─ $ sudo apt-get intall libssl-dev
    ┌─ (marslo@MarsloJiao ~) ->
    └─ $ dpkg -l | grep openssl
    ii  libcurl3:amd64                      7.35.0-1ubuntu2                            amd64        easy-to-use client-side URL transfer library (OpenSSL flavour)
    ii  libcurl4-openssl-dev:amd64          7.35.0-1ubuntu2                            amd64        development files and documentation for libcurl (OpenSSL flavour)
    ii  libgnutls-openssl27:amd64           2.12.23-12ubuntu2.1                        amd64        GNU TLS library - OpenSSL wrapper
    ii  openssl                             1.0.1f-1ubuntu2.4                          amd64        Secure Sockets Layer toolkit - cryptographic utility
    ii  python-openssl                      0.13-2ubuntu6                              amd64        Python 2 wrapper around the OpenSSL library
    </code></pre>

### thread_native.h
- Error Description
    <pre><code>┌─ (marslo@MarsloJiao ~/Tools/SourceCode/Ruby/ruby-2.1.2/ext/openssl) ->
    └─ $ make
    make: *** No rule to make target `/thread_native.h`, needed by `ossl.o`. Stop.
    </code></pre>

- Solution
    Add `top_srcdir=../..` into Makefile (the 63th line as below)
    <pre><code>┌─ (marslo@MarsloJiao ~/Tools/SourceCode/Ruby/ruby-2.1.2/ext/openssl) ->
    └─ $ grep top_srcdir Makefile -n
    63: top_srcdir=../..
    279: ossl.o: $(top_srcdir)/thread_native.h $(top_srcdir)/thread_$(THREAD_MODEL).h
    </code></pre>
