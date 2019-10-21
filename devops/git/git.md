Git Command Study and practice
=======

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Appoint](#appoint)
  - [Git Alias](#git-alias)
  - [.marslorc](#marslorc)
- [log](#log)
  - [show files and status without comments](#show-files-and-status-without-comments)
- [update](#update)
  - [fetch merge all](#fetch-merge-all)
  - [fetchall <branch>](#fetchall-branch)
- [Rebase](#rebase)
  - [Without Confilite file](#without-confilite-file)
  - [With Confilite file](#with-confilite-file)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Appoint
### [Git Alias](https://github.com/Marslo/LinuxStuff/blob/master/Configs/HOME/Git/.gitconfig)
```bash
st = status
ci = commit -am
br = branch
plog = log --max-count=3 --color --graph
 --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(blue)<%an>%Creset'
 --abbrev-commit --date=relative
plogs = log --color --graph
 --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(blue)<%an>%Creset'
 --abbrev-commit --date=relative
rlog = !bash -c 'git fetch && git plog remotes/origin/master'
rlogs = !bash -c 'git fetch && git plogs remotes/origin/master'
info = !bash -c '. ~/.marslo/.marslorc && gitinfo'
```

### .marslorc
- [.marslorc](https://raw.githubusercontent.com/marslo/mylinux/master/Configs/HOME/.marslo/.marslorc)

## log
### show files and status without comments
```bash
$ git log --color --stat --abbrev-commit --date=relative --graph --submodule --format="%H"

# or
$ git log --color --stat --abbrev-commit --date=relative --graph --submodule --format="%h %ad- %s [%an]"
```

## update
### fetch merge all
```bash
$ cat ~/.gitconfig
...
[alias]
  fma         = "!bash -c 'while read branch; do \n\
                   git fetch --all --force; \n\
                   git rebase -v refs/remotes/origin/${branch}; \n\
                   git merge --all --progress refs/remotes/origin/${branch}; \n\
                   git remote prune origin; \n\
                   if git --no-pager config --file $(git rev-parse --show-toplevel)/.gitmodules --get-regexp url; then \n\
                     git submodule sync --recursive; \n\
                     git submodule update --init --recursive \n\
                   fi \n\
                 done < <(git rev-parse --abbrev-ref HEAD) '"
...
```

### fetchall <branch>
```bash
$ cat ~/.marslorc
...
function fetchall()
{
  if [ 1 -eq $# ]; then
    brName=$1
  else
    brName="development"
  fi
  for i in $(${LS} -1d */); do
    gitFetch "$i" "$brName"
  done
}

function gitFetch() {
  GITDIR=${1%%/}
  GITBRANCH=$2
  ISStashed=false
  pushd . > /dev/null
  cd "${GITDIR}"
  echo -e "\\033[34m=== ${GITDIR} ===\\033[0m"

  if git rev-parse --git-dir > /dev/null 2>&1; then
    utFiles=$(git ls-files --others --exclude-standard)
    mdFiles=$(git ls-files --modified)
    cBranch=$(git rev-parse --abbrev-ref HEAD)
    [ ! -z "${utFiles}" ] && echo -e "\\033[35mUNTRACKED FILES in ${cBranch}: ${utFiles}\\033[0m"

    if ! git branch -a | ${GREP} "${GITBRANCH}" > /dev/null 2>&1; then
      GITBRANCH=master
    fi
    echo -e "\\033[33m~> ${GITBRANCH}\\033[0m"

    # checkout branch to $GITBRANCH
    if [ ! "${cBranch}" = "${GITBRANCH}" ]; then
      if [ ! -z "${mdFiles}" ]; then
        echo -e "\\033[31mGIT STASH: ${GITDIR} : ${cBranch} !!\\033[0m"
        git stash save "auto-stashed by gitFetch command"
        ISStashed=true
      fi
      git checkout "${GITBRANCH}"
    fi

    # remove the local branch if the branch has been deleted in remote
    if git remote prune origin --dry-run | ${GREP} prune; then
      prBranch=$(git remote prune origin --dry-run | ${GREP} prune | awk -F'origin/' '{print $NF}')
      if [ "${cBranch}" = "${prBranch}" ] && [ -z "${mdFiles}" ]; then
        echo -e "\\033[32mThe current branch ${cBranch} has been rmeoved in remote. And the current branch has no modified files!\\033[0m"
        ISStashed=false
      fi

      if git branch | ${GREP} "${prBranch}"; then
        echo -e "\\033[35mREMOVE LOCAL BRNACH ${prBranch}, due to ${prBranch} has been rmeoved in remote.\\033[0m"
        if ! git branch -D "${prBranch}"; then
          echo -e "\\033[32mWARNING: REMOVE LOCAL BRANCH ${prBranch} failed!!\\033[0m"
        fi
      fi
    fi

    # git fetchall on ${GITBRANCH}
    git fetch origin --prune
    git fetch --all --force
    git rebase -v --all refs/remotes/origin/${GITBRANCH}
    git merge --all --progress refs/remotes/origin/${GITBRANCH}
    git remote prune origin

    if git --no-pager config --file "$(git rev-parse --show-toplevel)/.gitmodules" --get-regexp url; then
      git submodule sync --recursive
      git submodule update --init --recursive
    fi

    # restore the current working branch
    if ${ISStashed}; then
      git checkout "${cBranch}"
      git stash pop
      echo -e "\\033[35mGIT STASH POP: ${GITDIR} : ${cBranch}\\033[0m"
    fi
  else
    echo -e "\\033[33mNOT Git Repo!!\\033[0m"
  fi
  popd > /dev/null
}
...
```

## Rebase

### Without Confilite file
#### Precondiction
```bash
$ git plog
37a0595 - (HEAD, master) 2: 2.txt (5 seconds ago) <Marslo>
1d9bcce - Initial commit (65 minutes ago) <Marslo>

$ git rlog
4e3106e - (origin/master, origin/HEAD) 1: 1.txt (2 minutes ago) <Marslo>
1d9bcce - Initial commit (65 minutes ago) <Marslo>

$ git br
  master

$ git push
To git@github.com:Marslo/GitStudy.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:Marslo/GitStudy.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
hint: before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

#### Merge with rebase
##### Use command: git pulll --rebase
```bash
$ git pull --rebase
First, rewinding head to replay your work on top of it...
Applying: 2: 2.txt
```

##### Check the status after pull rebase
- Check the status

    - The status of meraged file hasn't been changed
    ```bash
    $ git st
    # On branch master
    # Your branch is ahead of 'origin/master' by 1 commit.
    #   (use "git push" to publish your local commits)
    #
    nothing to commit, working directory clean
    ```

    - The branch hasn't been changed
    ```bash
    $ git br
      master
    ```

    - Log added the remote new version
    ```bash
    $ git plog
    7bc54e0 - (HEAD, master) 2: 2.txt (12 seconds ago) <Marslo>
    4e3106e - (origin/master, origin/HEAD) 1: 1.txt (4 minutes ago) <Marslo>
    1d9bcce - Initial commit (68 minutes ago) <Marslo>

    $ git rlog
    4e3106e - (origin/master, origin/HEAD) 1: 1.txt (4 minutes ago) <Marslo>
    1d9bcce - Initial commit (68 minutes ago) <Marslo>
    ```

### With Confilite file
#### Precondiction
```bash
$ git plog
 94a5935 - (HEAD, master) 2: 1 (25 seconds ago) <Marslo>
 1d9bcce - Initial commit (25 minutes ago) <Marslo>

$ git rlog
b9709fe - (origin/master, origin/HEAD) 1: 1 (71 seconds ago) <Mar
1d9bcce - Initial commit (25 minutes ago) <Marslo>

$ git br
  master

$ git push
To git@github.com:Marslo/GitStudy.git
 ! [rejected]        master -> master (non-fast-forward)
error: failed to push some refs to 'git@github.com:Marslo/GitStudy.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Merge the remote changes (e.g. 'git pull')
hint: before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

#### Merge by rebase
##### Using command: git pull --rebase
```bash
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
```

##### Check the status after pull rebase
- branch is changed (`master` -> `no branch`)
```bash
$ git br
  (no branch, rebasing master)
  master
```

- Status from `unchanged` and `staged` -> `Umerged`
```bash
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
```

- Log changed:
    - New committed version has been **removed**
    - Remote new version has been **added*

    ```bash
    $ git rlog
    b9709fe - (HEAD, origin/master, origin/HEAD) 1: 1 (2 minutes ago)
    1d9bcce - Initial commit (26 minutes ago) <Marslo>

    $ git plog
    b9709fe - (HEAD, origin/master, origin/HEAD) 1: 1 (2 minutes ago)
    1d9bcce - Initial commit (26 minutes ago) <Marslo>
    ```

- The confilicted file has been meraged
    ```bash
    $ git add .

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

    $ git br
      (no branch, rebasing master)
      master

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
    ```

#### Return to master branch
```bash
$ git rebase --continue
Applying: 2: 1
```

- Check the status
    - The merged file (`Unmerged`) -> `staged`
    ```bash
    $ git st
    # On branch master
    # Your branch is ahead of 'origin/master' by 1 commit.
    #   (use "git push" to publish your local commits)
    #
    nothing to commit, working directory clean
    ```

    - Log added the remote new version
    ```bash
    $ git plog
    d6962d6 - (HEAD, master) 2: 1 (4 seconds ago) <Marslo>
    b9709fe - (origin/master, origin/HEAD) 1: 1 (3 minutes ago) <Marslo>
    1d9bcce - Initial commit (27 minutes ago) <Marslo>

    $ git rlog
    b9709fe - (origin/master, origin/HEAD) 1: 1 (3 minutes ago) <Marslo>
    1d9bcce - Initial commit (27 minutes ago) <Marslo>
    ```

    - Branch changed `no branch, rebasing master` -> `master`
    ```bash
    $ git br
      master
    ```
