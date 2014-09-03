- `no refs in common and none specified; doing nothing.`
    - Error
        <pre><code>┌─ (marslo@MarsloJiao ~/Tools/Git/LaunchySkins) ->
        └─ $ git push
        No refs in common and none specified; doing nothing.
        Perhaps you should specify a branch such as 'master'.
        Everything up-to-date
        </code></pre>

  - Solution: `git push -u origin master`
      <pre><code>┌─ (marslo@MarsloJiao ~/Tools/Git/LaunchySkins) ->
      └─ $ git push -u origin master
      Counting objects: 40, done.
      Delta compression using up to 4 threads.
      Compressing objects: 100% (40/40), done.
      Writing objects: 100% (40/40), 133.46 KiB | 0 bytes/s, done.
      Total 40 (delta 6), reused 0 (delta 0)
      To git@github.com:Marslo/LaunchySkins.git
      \* [new branch]      master -> master
      \* Branch master set up to track remote branch master from origin.
      </code></pre>

## For CentOS
### /bin/sh: cc
    - Error:

        ┌─ (marslo@MarsloJiao ~/Marslo/Tools/git) ->
        └─ $ make prefix=/usr/local/myprograms/git
        GIT_VERSION = 2.1.0
            * new build flags
            CC credential-store.o
        /bin/sh: cc: command not found
        make: *** [credential-store.o] Error 127

    - Solution:

        ┌─ (marslo@MarsloJiao ~/Marslo/Tools/git) ->
        └─ $ yum install gcc gcc-g++ g++ make

### openssl/ssl.h
    - Error:

        ┌─ (marslo@MarsloJiao ~/Marslo/Tools/git) ->
        └─ $ make prefix=/usr/local/myprograms/git
            CC credential-store.o
        In file included from cache.h:4,
                         from credential-store.c:1:
        git-compat-util.h:213:25: warning: openssl/ssl.h: No such file or directory
        git-compat-util.h:214:25: warning: openssl/err.h: No such file or directory
        git-compat-util.h:326:25: warning: openssl/evp.h: No such file or directory
        git-compat-util.h:327:26: warning: openssl/hmac.h: No such file or directory
        git-compat-util.h:329:28: warning: openssl/x509v3.h: No such file or directory
        In file included from credential-store.c:1:
        cache.h:12:21: warning: openssl/sha.h: No such file or directory
        cache.h:20:18: warning: zlib.h: No such file or directory
        In file included from credential-store.c:1:
        cache.h:22: error: expected specifier-qualifier-list before ‘z_stream’
        make: *** [credential-store.o] Error 1

    - Solution:

        ┌─ (marslo@MarsloJiao ~/Marslo/Tools/git) ->
        └─ $ yum install openssl openssl-devel zlib-devel libcurl libcurl-devel

