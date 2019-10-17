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
