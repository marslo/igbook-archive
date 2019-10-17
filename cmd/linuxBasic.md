<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Brace Expansion](#brace-expansion)
  - [Multiple Directories Createion](#multiple-directories-createion)
  - [Copy a File to Multipule Folder](#copy-a-file-to-multipule-folder)
  - [Scp Multipule Folder/File to Target Server](#scp-multipule-folderfile-to-target-server)
- [CentOS](#centos)
  - [Yum](#yum)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# [Brace Expansion](https://www.gnu.org/software/bash/manual/html_node/Brace-Expansion.html)
## Multiple Directories Createion

```bash
$ mkdir sa{1..50}
$ mkdir -p sa{1..50}/sax{1..50}
$ mkdir {a-z}12345
$ mkdir {1,2,3}
$ mkdir test{01..10}
$ mkdir -p `date '+%y%m%d'`/{1,2,3}
$ mkdir -p $USER/{1,2,3}
```

## Copy a File to Multipule Folder

```bash
$ echo dir1 dir2 dir3 | xargs -n 1 cp file1
# OR
$ echo dir{1..10} | xargs -n 1 cp file1
```


## Scp Multipule Folder/File to Target Server

```bash
$ scp -r `echo dir{1..10}` user@target.server:/target/server/path/
```

# CentOS
## Yum
### `File "/usr/libexec/urlgrabber-ext-down", line 28`
- Error

        File "/usr/libexec/urlgrabber-ext-down", line 28
        except OSError, e:
                      ^

- Solution

    ```bash
    $ sudo update-alternatives --remove python /usr/bin/python3
    $ realpath /usr/bin/python
    /usr/bin/python2.7
    ```

OR

    ```bash
    $ sudo update-alternatives --config python

    There are 3 programs which provide 'python'.

      Selection    Command
    -----------------------------------------------
    *+ 1           /usr/bin/python3
       2           /usr/bin/python2.7
       3           /usr/bin/python2

    Enter to keep the current selection[+], or type selection number: 3
    ```


- [Reason](https://www.linuxquestions.org/questions/linux-newbie-8/yum-upgrading-error-4175632414/) 

    ```bash
    $ ls -l /usr/bin/python*
    lrwxrwxrwx 1 root root    24 Jul 10 02:29 /usr/bin/python -> /etc/alternatives/python
    lrwxrwxrwx 1 root root     9 Dec  6  2018 /usr/bin/python2 -> python2.7
    -rwxr-xr-x 1 root root  7216 Oct 30  2018 /usr/bin/python2.7
    lrwxrwxrwx 1 root root     9 Mar  7  2019 /usr/bin/python3 -> python3.4
    -rwxr-xr-x 2 root root 11392 Feb  5  2019 /usr/bin/python3.4
    -rwxr-xr-x 2 root root 11392 Feb  5  2019 /usr/bin/python3.4m

    $ ls -altrh /etc/alternatives/python
    lrwxrwxrwx 1 root root 16 Jul 10 02:29 /etc/alternatives/python -> /usr/bin/python3
    ```

- reference
    - [Yum install error file "/usr/bin/yum", line 30](http://www.programmersought.com/article/3242669414/)
    - [failed at yum update and how to fix it](http://wenhan.blog/2018/02/18/failed-at-yum-update-and-how-to-fix-it/)
    - [Upgraded Python, and now I can't run “yum upgrade”](https://unix.stackexchange.com/questions/524552/upgraded-python-and-now-i-cant-run-yum-upgrade)

# Utils
### Get Interface by command
```bash
interface=$(netstat -nr | grep -E 'UG|UGSc' | grep -E '^0.0.0|default' | grep -E '[0-9.]{7,15}' | awk -F' ' '{print $NF}')
# or
interface=$(ip route get $(nslookup github.com | grep Server | awk -F' ' '{print $NF}') | sed -rn 's|.*dev\s+(\S+)\s+src.*$|\1|p') # get the route to github
```

### get ipv4 address
```bash
ipAddr=$(ip a s "${interface}" | sed -rn 's|.*inet ([0-9\.]{7,15})/[0-9]{2} brd.*$|\1|p')
```

### disable firewall
```bash
$ sudo systemctl stop firewalld
$ sudo systemctl disable firewalld
$ sudo systemctl mask firewalld
```

- check result
```bash
$ sudo systemctl is-enabled firewalld
$ sudo systemctl is-active firewalld
$ sudo firewall-cmd --state
```

### change net.bridge
```bash
$ sudo modprobe br_netfilter
$ sudo sysctl net.bridge.bridge-nf-call-iptables=1
$ sudo sysctl net.bridge.bridge-nf-call-ip6tables=1

# OR

$ sudo bash -c "cat >  /etc/sysctl.d/k8s.conf" << EOF
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
EOF
```
- check status
```bash
$ sudo sysctl --system
```

### off swap

```bash
$ sudo swapoff -a
$ sudo bash -c "${SED} -e 's:^\\(.*swap.*\\)$:# \\1:' -i /etc/fstab"
```

### disable selinux
```bash
$ setenforce 0
$ sudo bash -c "${SED} 's/^SELINUX=enforcing$/SELINUX=permissive/' -i /etc/selinux/config"
```
