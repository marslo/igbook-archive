### ssl.h
- Problem:
    <pre><code>git-compat-util.h:213:25: fatal error: openssl/ssl.h: No such file or directory
    #include \<openssl/ssl.h\>
    </code></pre>
- Soluction:
    <pre><code>$ sudo apt-get install libssl-dev</code></pre>

### curl.h
- Problem:
    <pre><code>http.h:6:23: fatal error: curl/curl.h: No such file or directory
    #include \<curl/curl.h\>
    </code></pre>
- Soluction:
    - For OpenSuse:
    <pre><code>$ sudo apt-get install libcurl4-openssl</code></pre>
    - For Ubuntu:
    <pre><code>$ sudo apt-get install libcurl4-openssl-dev</code></pre>

- Reason:
    `libcurl-dev` should be installed, but 
    <pre><code>Package libcurl-dev is a virtual package provided by:
      libcurl4-openssl-dev 7.35.0-1ubuntu2
      libcurl4-nss-dev 7.35.0-1ubuntu2
      libcurl4-gnutls-dev 7.35.0-1ubuntu2
    You should explicitly select one to install.
    </code></pre>
### expat.h
- Problem:
    <pre><code>http-push.c:17:19: fatal error: expat.h: No such file or directory
    #include \<expat.h\>
    </code></pre>
- Soluction:
    <pre><code>$ apt-cache search expat | grep dev
    libexpat1-dev - XML parsing C library - development kit
    lib64expat1-dev - XML parsing C library - development kit (64bit)
    libexpat-ocaml-dev - OCaml expat bindings
    lua-expat-dev - libexpat development files for the Lua language
    tdom-dev - fast XML/DOM/XPath/XSLT extension for Tcl written in C (development files)
    $ sudo apt-get install libexpat1-dev
    </code></pre>
