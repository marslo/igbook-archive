<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

# Content
- [Content](#content)
  - [Multiple Directories Createion](#multiple-directories-createion)
  - [Copy a File to Multipule Folder](#copy-a-file-to-multipule-folder)
  - [Scp Multipule Folder/File to Target Server](#scp-multipule-folderfile-to-target-server)
- [CentOS](#centos)
  - [Yum](#yum)
    - [`File "/usr/libexec/urlgrabber-ext-down", line 28`](#file-usrlibexecurlgrabber-ext-down-line-28)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


# [Brace Expansion](https://www.gnu.org/software/bash/manual/html_node/Brace-Expansion.html)
## Multiple Directories Createion

    mkdir sa{1..50}
    mkdir -p sa{1..50}/sax{1..50}
    mkdir {a-z}12345
    mkdir {1,2,3}
    mkdir test{01..10}
    mkdir -p `date '+%y%m%d'`/{1,2,3}
    mkdir -p $USER/{1,2,3}

## Copy a File to Multipule Folder

    echo dir1 dir2 dir3 | xargs -n 1 cp file1
    OR
    echo dir{1..10} | xargs -n 1 cp file1


## Scp Multipule Folder/File to Target Server

    scp -r `echo dir{1..10}` user@target.server:/target/server/path/

# CentOS
## Yum
### `File "/usr/libexec/urlgrabber-ext-down", line 28`
- Error

        File "/usr/libexec/urlgrabber-ext-down", line 28
        except OSError, e:
                      ^

- Solution

        $ sudo update-alternatives --remove python /usr/bin/python3
        $ realpath /usr/bin/python
        /usr/bin/python2.7

OR

		$ sudo update-alternatives --config python

		There are 3 programs which provide 'python'.

		  Selection    Command
		-----------------------------------------------
		*+ 1           /usr/bin/python3
		   2           /usr/bin/python2.7
		   3           /usr/bin/python2

		Enter to keep the current selection[+], or type selection number: 3


- [Reason](https://www.linuxquestions.org/questions/linux-newbie-8/yum-upgrading-error-4175632414/) ([failed at yum update and how to fix it](http://wenhan.blog/2018/02/18/failed-at-yum-update-and-how-to-fix-it/))

        $ ls -l /usr/bin/python*
        lrwxrwxrwx 1 root root    24 Jul 10 02:29 /usr/bin/python -> /etc/alternatives/python
        lrwxrwxrwx 1 root root     9 Dec  6  2018 /usr/bin/python2 -> python2.7
        -rwxr-xr-x 1 root root  7216 Oct 30  2018 /usr/bin/python2.7
        lrwxrwxrwx 1 root root     9 Mar  7  2019 /usr/bin/python3 -> python3.4
        -rwxr-xr-x 2 root root 11392 Feb  5  2019 /usr/bin/python3.4
        -rwxr-xr-x 2 root root 11392 Feb  5  2019 /usr/bin/python3.4m

        $ ls -altrh /etc/alternatives/python
        lrwxrwxrwx 1 root root 16 Jul 10 02:29 /etc/alternatives/python -> /usr/bin/python3

