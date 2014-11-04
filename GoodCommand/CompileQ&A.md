### ssl.h
- Problem:
    <pre><code>git-compat-util.h:213:25: fatal error: openssl/ssl.h: No such file or directory
    #include \<openssl/ssl.h\>
    </code></pre>
- Solution:
    - Ubuntu/Debian:

            $ sudo apt-get install libssl-dev
        
    - RHEL/CentOS

            $ sudo yum install openssl-devel

### curl.h
- Problem:

        http.h:6:23: fatal error: curl/curl.h: No such file or directory
        #include \<curl/curl.h\>

- Solution:
    - For OpenSuse:

            $ sudo apt-get install libcurl4-openssl

    - For Ubuntu/Debian:

            $ sudo apt-get install libcurl4-openssl-dev

    - For RHEL/CentOS:

            $ sudo yum install libcurl libcurl-devel

- Reason:
    `libcurl-dev` should be installed, but

        Package libcurl-dev is a virtual package provided by:
          libcurl4-openssl-dev 7.35.0-1ubuntu2
          libcurl4-nss-dev 7.35.0-1ubuntu2
          libcurl4-gnutls-dev 7.35.0-1ubuntu2
        You should explicitly select one to install.

### expat.h
- Problem:

        http-push.c:17:19: fatal error: expat.h: No such file or directory
        #include \<expat.h\>

- Solution:

        $ apt-cache search expat | grep dev
        libexpat1-dev - XML parsing C library - development kit
        lib64expat1-dev - XML parsing C library - development kit (64bit)
        libexpat-ocaml-dev - OCaml expat bindings
        lua-expat-dev - libexpat development files for the Lua language
        tdom-dev - fast XML/DOM/XPath/XSLT extension for Tcl written in C (development files)
        $ sudo apt-get install libexpat1-dev

### tclsh
- Problem:

        tclsh failed; using unoptimized loading
        MSGFMT    po/de.msg make[1]: *** [po/de.msg] Error 127
        make: *** [all] Error 2

- Solution:

        ┌─ (marslo@MJ ~/Tools/Software/Programming/Git/git-master) ->
        └─ $ sudo apt-get install gettext

### asciidoc
- Problem
    <pre><code>ASCIIDOC git-add.html
    /bin/sh: 2: asciidoc: not found
    make[1]: *** [git-add.html] Error 127
    make[1]: Leaving directory `/home/marslo/Tools/Software/Programming/Git/git-master/Documentation'
    make: *** [doc] Error 2
    </code></pre>

- Solution
    <pre><code>┌─ (marslo@MJ ~/Tools/Software/Programming/Git/git-master) ->
    └─ $ apt-cache search asciidoc
    ┌─ (marslo@MJ ~/Tools/Software/Programming/Git/git-master) ->
    └─ $ sudo apt-get install asciidoc
    </code></pre>

### docbook2x-texi
- Problem
    <pre><code>DB2TEXI user-manual.texi
    /bin/sh: 2: docbook2x-texi: not found
    make[1]: *** [user-manual.texi] Error 127
    make[1]: Leaving directory `/home/marslo/Tools/Software/Programming/Git/git-master/Documentation'
    make: *** [info] Error 2
    </code></pre>

- Solution
    <pre><code>┌─ (marslo@MJ ~/Tools/Software/Programming/Git/git-master) ->
    └─ $ sudo apt-get install docbook2x
    </code></pre>

### hunspell
- Problem
    <pre><code>┌─ (marslo@MarsloJiao ~/Tools/Git/goldendict) ->
    └─ $ qmake-qt4
    Project MESSAGE: Install Prefix is: /usr/local
    Project ERROR: Package hunspell not found
    </code></pre>

- Solution
    <pre><code>┌─ (marslo@MarsloJiao ~/Tools/Git/goldendict) ->
    └─ $ sudo apt-get install hunspell
    ┌─ (marslo@MarsloJiao ~/Tools/Git/goldendict) ->
    └─ $ sudo apt-get install libhunspell-dev
    </code></pre>

### ao
- Problem
    <pre><code>┌─ (marslo@MarsloJiao ~/Tools/Git/goldendict) ->
    └─ $ qmake-qt4
    Project MESSAGE: Install Prefix is: /usr/local
    Project ERROR: Package ao not found
    </code></pre>

- Solution
    <pre><code>┌─ (marslo@MarsloJiao ~/Tools/Git/goldendict) ->
    └─ $ acs ao | grep dev
    libao-dev - Cross Platform Audio Output Library Development
    ...
    ┌─ (marslo@MarsloJiao ~/Tools/Git/goldendict) ->
    └─ $ sudo apt-get install libao-dev
    </code></pre>

## For CentOS
### ncurses
- Problem
    <pre><code>no terminal library found
    checking for tgetent()... configure: error: NOT FOUND!
          You need to install a terminal library; for example ncurses.
          Or specify the name of the library with --with-tlib.
    </code></pre>

- Solution
    <pre><code>┌─ (marslo@MarsloJiao ~/Marslo/Tools/vim) ->
    └─ $ yum install ncurses-devel
    </code></pre>
