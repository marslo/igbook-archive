<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [.gitconfig](#gitconfig)
- [project.config](#projectconfig)
  - [get project.config](#get-projectconfig)
  - [publish to remote](#publish-to-remote)

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
```
