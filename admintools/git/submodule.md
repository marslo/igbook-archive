# submodule

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [git submodule](submodule.md#git-submodule)
  * [init submodule](submodule.md#init-submodule)
  * [update submodule](submodule.md#update-submodule)
  * [revert changes in submodule](submodule.md#revert-changes-in-submodule)
  * [working with submodule](submodule.md#working-with-submodule)
  * [remove submodule](submodule.md#remove-submodule)

## git submodule

> reference:
>
> * [gitmodules - Defining submodule properties](https://git-scm.com/docs/gitmodules)
> * [Gerrit Code Review - Superproject subscription to submodules updates](https://gerrit-review.googlesource.com/Documentation/user-submodules.html)[https://gerrit-review.googlesource.com/Documentation/user-submodules.html](https://gerrit-review.googlesource.com/Documentation/user-submodules.html)

### init submodule

```bash
$ git submodule add -b <BranchName> <SubRepoUrl> <NameInSuper>
$ git submodule init
$ git submodule update --init
```

### update submodule

```bash
$ git config -f .gitmodules submodule.<SubmoduleNameInSuperRepo>.branch <NewBranchName>
$ git submodule update --remote
```

### [revert changes in submodule](https://stackoverflow.com/a/27415757/2940319)

```bash
$ git submodule deinit -f .
$ git submodule update --init
```

* [or](https://stackoverflow.com/a/62792847/2940319)

  > [or](https://gist.github.com/nicktoumpelis/11214362)
  >
  > ```bash
  > $ git submodule foreach --recursive git clean -dffx
  > $ git submodule foreach --recursive git reset --hard
  > ```

### working with submodule

#### pull from remote

* update submodule only

  ```bash
  $ git submodule update --remote --recursive --force --rebase
  ```

* update both super and submodule

  ```bash
  $ git pull [--rebase] --recurse-submodules
  ```

#### push to remote

* push submodule only

  ```bash
  $ cd <SubFolder>
  $ git push --recurse-submodule=on-demand
  ```

* push for both super and submodule

  ```bash
  $ cd <SubFolder>
  $ git add --all
  $ git commit -am "<Comments for Sub>"
  $ git push --recurse-submodule=on-demand

  $ cd $(git rev-parse --show-superproject-working-tree)
  # or: https://stackoverflow.com/a/7359782/2940319
  $ cd $(git rev-parse --show-superproject-working-tree --show-toplevel | head -1)

  $ git add --all
  $ git commit -am "<Comments for Super>"
  $ git push origin $(git rev-parse --abbrev-ref HEAD)
  ```

### remove submodule

```bash
$ git rm --cached <SubmoudleName>
$ rm -rf <SubmodulePath>
$ rm -rf .gitmodules
$ rm -rf .git/modules/<SubmoduleName>
$ vim .git/config
```

