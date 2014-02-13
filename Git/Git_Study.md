Git Command Study and practice
=======

## Content

- [Appoint](https://github.com/Marslo/MyNotes/blob/master/Git/Git_Study.md#appoint)
    - [Git Aliases](https://github.com/Marslo/MyNotes/blob/master/Git/Git_Study.md#git-alias)
    - [.marslorc](https://github.com/Marslo/MyNotes/blob/master/Git/Git_Study.md#marslorc)

- [Rebase](https://github.com/Marslo/MyNotes/blob/master/Git/Git_Study.md#rebase)
    - [Without Confilite file](https://github.com/Marslo/MyNotes/blob/master/Git/Git_Study.md#without-confilite-file)
        - [Precondition](https://github.com/Marslo/MyNotes/blob/master/Git/Git_Study.md#precondiction)
        - [Merge with rebase](https://github.com/Marslo/MyNotes/blob/master/Git/Git_Study.md#merge-with-rebase)
    - [With Confilite file](https://github.com/Marslo/MyNotes/blob/master/Git/Git_Study.md#with-confilite-file)
        - [Precondicition](https://github.com/Marslo/MyNotes/blob/master/Git/Git_Study.md#precondiction-1)
        - [Merge by rebase](https://github.com/Marslo/MyNotes/blob/master/Git/Git_Study.md#merge-by-rebase)
        - [Return to master branch](https://github.com/Marslo/MyNotes/blob/master/Git/Git_Study.md#return-to-master-branch)


## Appoint
### [Git Alias](https://github.com/Marslo/LinuxStuff/blob/master/Configs/HOME/Git/.gitconfig)
- st = status
- ci = commit -am
- br = branch
- plog = log --max-count=3 --color --graph
 --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(blue)<%an>%Creset'
 --abbrev-commit --date=relative
- plogs = log --color --graph
 --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(blue)<%an>%Creset'
 --abbrev-commit --date=relative
- rlog = !bash -c 'git fetch && git plog remotes/origin/master'
- rlogs = !bash -c 'git fetch && git plogs remotes/origin/master'
- info = !bash -c '. ~/.marslo/.marslorc && gitinfo'

### .marslorc
- [.marslorc](https://github.com/Marslo/LinuxStuff/blob/master/Configs/HOME/.marslo/.marslorc)



## Rebase

### Without Confilite file
#### Precondiction
    <pre><code>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git plog
    37a0595 - (HEAD, master) 2: 2.txt (5 seconds ago) <Marslo>
    1d9bcce - Initial commit (65 minutes ago) <Marslo>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git rlog
    4e3106e - (origin/master, origin/HEAD) 1: 1.txt (2 minutes ago) <Marslo>
    1d9bcce - Initial commit (65 minutes ago) <Marslo>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git br
      master
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git push
    To git@github.com:Marslo/GitStudy.git
     ! [rejected]        master -> master (non-fast-forward)
    error: failed to push some refs to 'git@github.com:Marslo/GitStudy.git'
    hint: Updates were rejected because the tip of your current branch is behind
    hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
    hint: before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.
    </code></pre>

#### Merge with rebase
##### Use command: git pulll --rebase

    <pre><code>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git pull --rebase
    First, rewinding head to replay your work on top of it...
    Applying: 2: 2.txt
    </code></pre>

##### Check the status after pull rebase
- Check the status

    - The status of meraged file hasn't been changed
    <pre><code>[marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git st
    # On branch master
    # Your branch is ahead of 'origin/master' by 1 commit.
    #   (use "git push" to publish your local commits)
    #
    nothing to commit, working directory clean
    </code></pre>

    - The branch hasn't been changed
    <pre><code>[marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git br
      master
    </code></pre>

    - Log added the remote new version
    <pre><code>[marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git plog
    7bc54e0 - (HEAD, master) 2: 2.txt (12 seconds ago) <Marslo>
    4e3106e - (origin/master, origin/HEAD) 1: 1.txt (4 minutes ago) <Marslo>
    1d9bcce - Initial commit (68 minutes ago) <Marslo>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git rlog
    4e3106e - (origin/master, origin/HEAD) 1: 1.txt (4 minutes ago) <Marslo>
    1d9bcce - Initial commit (68 minutes ago) <Marslo>
    </code></pre>

### With Confilite file
#### Precondiction

    <pre><code>
    marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git plog
     94a5935 - (HEAD, master) 2: 1 (25 seconds ago) <Marslo>
     1d9bcce - Initial commit (25 minutes ago) <Marslo>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git rlog
    b9709fe - (origin/master, origin/HEAD) 1: 1 (71 seconds ago) <Mar
    1d9bcce - Initial commit (25 minutes ago) <Marslo>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git br
      master
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git push
    To git@github.com:Marslo/GitStudy.git
     ! [rejected]        master -> master (non-fast-forward)
    error: failed to push some refs to 'git@github.com:Marslo/GitStudy.git'
    hint: Updates were rejected because the tip of your current branch is behind
    hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
    hint: before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.
    </code></pre>

#### Merge by rebase
##### Using command: git pull --rebase

    <pre><code>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git pull --rebase
    First, rewinding head to replay your work on top of it...
    Applying: 2: 1
    Using index info to reconstruct a base tree...
    M       README.md
    Falling back to patching base and 3-way merge...
    Auto-merging README.md
    CONFLICT (content): Merge conflict in README.md
    Failed to merge in the changes.
    Patch failed at 0001 2: 1
    The copy of the patch that failed is found in:
       /home/marslo/Tools/Git/2_GitStudy/.git/rebase-apply/patch
    When you have resolved this problem, run "git rebase --continue".
    If you prefer to skip this patch, run "git rebase --skip" instead.
    To check out the original branch and stop rebasing, run "git rebase --abort".
    </code></pre>

##### Check the status after pull rebase
- branch is changed (`master` -> `no branch`)

    <pre><code>[marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git br
      (no branch, rebasing master)
      master
    </code></pre>

- Status from `unchanged` and `staged` -> `Umerged`
    <pre><code>[marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git st
    # HEAD detached at b9709fe
    # You are currently rebasing branch 'master' on 'b9709fe'.
    #   (fix conflicts and then run "git rebase --continue")
    #   (use "git rebase --skip" to skip this patch)
    #   (use "git rebase --abort" to check out the original branch)
    #
    # Unmerged paths:
    #   (use "git reset HEAD <file>..." to unstage)
    #   (use "git add <file>..." to mark resolution)
    #
    #       both modified:      README.md
    #
    no changes added to commit (use "git add" and/or "git commit -a")
    </code></pre>

- Log changed:
    - New committed version has been **removed**
    - Remote new version has been **added*
    <pre><code>[marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git rlog
    b9709fe - (HEAD, origin/master, origin/HEAD) 1: 1 (2 minutes ago)
    1d9bcce - Initial commit (26 minutes ago) <Marslo>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git plog
    b9709fe - (HEAD, origin/master, origin/HEAD) 1: 1 (2 minutes ago)
    1d9bcce - Initial commit (26 minutes ago) <Marslo>
    </code></pre>

- The confilicted file has been meraged
    <pre><code>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git add .
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git st
    # HEAD detached at b9709fe
    # You are currently rebasing branch 'master' on 'b9709fe'.
    #   (all conflicts fixed: run "git rebase --continue")
    #
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    #       modified:   README.md
    #
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git br
      (no branch, rebasing master)
      master
    [marslo@MJ ~/Tools/2_GitStudy]
    $ git diff --staged
    diff --git a/README.md b/README.md
    index b1acca3..12afed2 100644
    --- a/README.md
    +++ b/README.md
    @@ -1 +1,5 @@
    +<<<<<<< HEAD
     1: 1
    +=======
    +2: 1
    +>>>>>>> 2: 1
    </code></pre>

#### Return to master branch

    <pre><code>
    marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git rebase --continue
    Applying: 2: 1
    </code></pre>

- Check the status
    - The merged file (`Unmerged`) -> `staged`
    <pre><code>[marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git st
    # On branch master
    # Your branch is ahead of 'origin/master' by 1 commit.
    #   (use "git push" to publish your local commits)
    #
    nothing to commit, working directory clean
    </code></pre>

    - Log added the remote new version
    <pre><code>[marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git plog
    d6962d6 - (HEAD, master) 2: 1 (4 seconds ago) <Marslo>
    b9709fe - (origin/master, origin/HEAD) 1: 1 (3 minutes ago) <Marslo>
    1d9bcce - Initial commit (27 minutes ago) <Marslo>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git rlog
    b9709fe - (origin/master, origin/HEAD) 1: 1 (3 minutes ago) <Marslo>
    1d9bcce - Initial commit (27 minutes ago) <Marslo>
    </code></pre>

    - Branch changed `no branch, rebasing master` -> `master`
    <pre><code>[marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git br
      master
    </code></pre>
