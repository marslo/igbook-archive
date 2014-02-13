Git Command Study and practice

## Rebase
### Without Confilite
### With Confilite
#### Precondiction

    marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git plog
    * 94a5935 - (HEAD, master) 2: 1 (25 seconds ago) <Marslo>
    * 1d9bcce - Initial commit (25 minutes ago) <Marslo>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git rlog
    * b9709fe - (origin/master, origin/HEAD) 1: 1 (71 seconds ago) <Mar
    * 1d9bcce - Initial commit (25 minutes ago) <Marslo>
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git br
    * master
    [marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git push
    To git@github.com:Marslo/GitStudy.git
     ! [rejected]        master -> master (non-fast-forward)
    error: failed to push some refs to 'git@github.com:Marslo/GitStudy.git'
    hint: Updates were rejected because the tip of your current branch is behind
    hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
    hint: before pushing again.
    hint: See the 'Note about fast-forwards' in 'git push --help' for details.

#### Merge by rebase
##### Using command: git pull --rebase

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

##### Check the status after pull rebase
- branch is changed (`master` -> `no branch`)

        [marslo@MJ ~/Tools/Git/2_GitStudy]
        $ git br
        * (no branch, rebasing master)
          master

- Status from `unchanged` and `staged` -> `Umerged`

        [marslo@MJ ~/Tools/Git/2_GitStudy]
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

- Log changed:
    - New committed version has been **removed**
    - Remote new version has been **added*

        [marslo@MJ ~/Tools/Git/2_GitStudy]
        $ git rlog
        * b9709fe - (HEAD, origin/master, origin/HEAD) 1: 1 (2 minutes ago)
        * 1d9bcce - Initial commit (26 minutes ago) <Marslo>
        [marslo@MJ ~/Tools/Git/2_GitStudy]
        $ git plog
        * b9709fe - (HEAD, origin/master, origin/HEAD) 1: 1 (2 minutes ago)
        * 1d9bcce - Initial commit (26 minutes ago) <Marslo>

- The confilicted file has been meraged

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
        * (no branch, rebasing master)
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

#### Return to master branch

    marslo@MJ ~/Tools/Git/2_GitStudy]
    $ git rebase --continue
    Applying: 2: 1

- Check the status
    - The merged file (`Unmerged`) -> `staged`

          marslo@MJ ~/Tools/Git/2_GitStudy]
          $ git st
          # On branch master
          # Your branch is ahead of 'origin/master' by 1 commit.
          #   (use "git push" to publish your local commits)
          #
          nothing to commit, working directory clean

    - Log: added the remote new version

        [marslo@MJ ~/Tools/Git/2_GitStudy]
        $ git plog
        * d6962d6 - (HEAD, master) 2: 1 (4 seconds ago) <Marslo>
        * b9709fe - (origin/master, origin/HEAD) 1: 1 (3 minutes ago) <Mars
        * 1d9bcce - Initial commit (27 minutes ago) <Marslo>
        [marslo@MJ ~/Tools/Git/2_GitStudy]
        $ git rlog
        * b9709fe - (origin/master, origin/HEAD) 1: 1 (3 minutes ago) <Mars
        * 1d9bcce - Initial commit (27 minutes ago) <Marslo>

    - Branch changed: `no branch, rebasing master` -> `master`

        [marslo@MJ ~/Tools/Git/2_GitStudy]
        $ git br
        * master
