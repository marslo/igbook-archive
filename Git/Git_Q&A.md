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
       * [new branch]      master -> master
       * Branch master set up to track remote branch master from origin.
      </code></pre>
