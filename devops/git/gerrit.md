<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [.gitconfig](#gitconfig)
- [project.config](#projectconfig)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

### .gitconfig
```bash
$ git config --global gitreview.username <UserName>
$ git config --global gitreview.remote origin
```
### project.config

#### get project.config
```bash
$ git clone <repo url>
# or update the local repo to HEAD
$ git pull [--rebase]

$ git fetch origin refs/meta/config:refs/remotes/origin/meta/config
$ git checkout meta/config
```

#### publish to remote
```bash
$ git add --all .
$ git commit -m "<add your comments here>"
```
- submit directly
```bash
$ git push origin meta/config:meta/config
# OR
$ git push origin HEAD:refs/meta/config
```
- submit review
```bash
$ git push origin HEAD:refs/for/refs/meta/config
# or
$ git push origin meta/config:refs/for/refs/meta/config
```

#### update meta/config if remotes update
```bash
$ git fetch origin --force refs/meta/config:refs/remotes/origin/meta/config

$ git pull origin refs/meta/config
# or
$ git merge meta/config
```

#### useful refs
- `refs/heads/sandbox/${username}/*`
- `refs/heads/jira/jira-[0-9]{1,5}(_.*)?`
- freeze `master` branch
    ```bash
    [access "refs/for/refs/heads/master"]
    push = block group user/Marslo Jiao (marslo)
    submit = block group group user/Marslo Jiao (marslo)
    addPatchSet = block group user/Marslo Jiao (marslo)
    pushMerge = block group user/Marslo Jiao (marslo)
    ```
