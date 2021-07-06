# tricky

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [copy path](tricky.md#copy-path)
  * [copy STDOUT into clipboard](tricky.md#copy-stdout-into-clipboard)
  * [Copy path from finder](tricky.md#copy-path-from-finder)
* [create an app for script](tricky.md#create-an-app-for-script)
  * [get standalone commands for the script](tricky.md#get-standalone-commands-for-the-script)
  * [using Automator.app to create an app](tricky.md#using-automatorapp-to-create-an-app)
  * [edit `Contents/Info.plist`](tricky.md#edit-contentsinfoplist)
  * [create script to open the groovyConsole](tricky.md#create-script-to-open-the-groovyconsole)
  * [set the icon for new app](tricky.md#set-the-icon-for-new-app)
  * [move `groovyConsole.app` to `/Application`](tricky.md#move-groovyconsoleapp-to-application)
* [add snippets for input](tricky.md#add-snippets-for-input)
  * [enable Technical Symbols](tricky.md#enable-technical-symbols)
  * [And snippets](tricky.md#and-snippets)
  * [finally](tricky.md#finally)
* [others](tricky.md#others)
  * [shutdown mac via commands](tricky.md#shutdown-mac-via-commands)
  * [turn off the screen without sleeping](tricky.md#turn-off-the-screen-without-sleeping)
  * [launch apps](tricky.md#launch-apps)
  * [extra pkg](tricky.md#extra-pkg)
  * [create image](tricky.md#create-image)
  * [disk](tricky.md#disk)
  * [disable startup music](tricky.md#disable-startup-music)
  * [3D lock screen](tricky.md#3d-lock-screen)
  * [take screenshot after 3 sec](tricky.md#take-screenshot-after-3-sec)
  * [setup welcome text in login screen](tricky.md#setup-welcome-text-in-login-screen)
  * [show message on desktop](tricky.md#show-message-on-desktop)
  * [modify font in plist](tricky.md#modify-font-in-plist)
  * [show process details](tricky.md#show-process-details)

## copy path

### copy STDOUT into clipboard

> \[!NOTE\]
>
> * `pbcopy` for macOS
> * `xclip` for Linux

```bash
$ <cmd> | pbcopy
```

* example

  ```bash
  $ cat file | pbcopy
  $ pwd | pbcopy
  ```

### Copy path from finder

* [_right-click_\(control + left-click\) -&gt; option](https://osxdaily.com/2013/06/19/copy-file-folder-path-mac-os-x/)

![option key](../.gitbook/assets/copy-path-optional-key.png)

* Automator -&gt; Quick Action

![create quick action](../.gitbook/assets/copy-path-service-1.png)

![content menu](../.gitbook/assets/copy-path-service-2.png)

* [Automator -&gt; Apple Script](https://apple.stackexchange.com/a/47234/254265)

  ```bash
  on run {input, parameters}

    try
      tell application "Finder" to set the clipboard to POSIX path of (target of window 1 as alias)
    on error
      beep
    end try

    return input
  end run
  ```

![copy path apple script](../.gitbook/assets/copy-path-applescript.png)

![copy path shortcut key](../.gitbook/assets/copy-path-shortcut.png)

## create an app for script

> case: run `groovyConsole` from Spolite or Alfred reference: [Install groovy console on Mac and make it runnable from dock](https://superuser.com/a/1303372/112396)

### get standalone commands for the script

```bash
$ ps aux | grep groovyConsole | grep -v grep
marslo           50495   0.0  3.4 11683536 577828   ??  S     5:50PM   0:15.85 /Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/bin/java -Xdock:name=GroovyConsole -Xdock:icon=/usr/local/opt/groovy/libexec/lib/groovy.icns -Dgroovy.jaxb=jaxb -classpath /usr/local/opt/groovy/libexec/lib/groovy-3.0.6.jar -Dscript.name=/usr/local/opt/groovy/libexec/bin/groovyConsole -Dprogram.name=groovyConsole -Dgroovy.starter.conf=/usr/local/opt/groovy/libexec/conf/groovy-starter.conf -Dgroovy.home=/usr/local/opt/groovy/libexec -Dtools.jar=/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/lib/tools.jar org.codehaus.groovy.tools.GroovyStarter --main groovy.console.ui.Console --conf /usr/local/opt/groovy/libexec/conf/groovy-starter.conf --classpath .:/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/lib/tools.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/lib/dt.jar:/usr/local/opt/groovy/libexec/lib:.
```

==&gt; which would be:

```bash
/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/bin/java \
        -Xdock:name=GroovyConsole \
        -Xdock:icon=/usr/local/opt/groovy/libexec/lib/groovy.icns \
        -Dgroovy.jaxb=jaxb \
        -classpath /usr/local/opt/groovy/libexec/lib/groovy-3.0.6.jar \
        -Dscript.name=/usr/local/opt/groovy/libexec/bin/groovyConsole \
        -Dprogram.name=groovyConsole \
        -Dgroovy.starter.conf=/usr/local/opt/groovy/libexec/conf/groovy-starter.conf \
        -Dgroovy.home=/usr/local/opt/groovy/libexec \
        -Dtools.jar=/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/lib/tools.jar org.codehaus.groovy.tools.GroovyStarter \
        --main groovy.console.ui.Console \
        --conf /usr/local/opt/groovy/libexec/conf/groovy-starter.conf \
        --classpath .:/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/lib/tools.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/lib/dt.jar:/usr/local/opt/groovy/libexec/lib:.
```

### using Automator.app to create an app

* Open **Automator.app** » **New** » **Application**

  ![Automator.app &#xBB; select Applicaiton](../.gitbook/assets/runable-app-1.png)

* Select **Run Shell Script** » save to .app with empty shell script ![Automator.app &#xBB; select Run Shell Script](../.gitbook/assets/runable-app-2.png)

  ![Automator.app &#xBB; save to an app](../.gitbook/assets/runable-app-3.png)

### edit `Contents/Info.plist`

```bash
$ vim groovyConsole.app/Contents/Info.plist
...
<key>CFBundleExecutable</key>
<string>gConsole</string>           « the script name, can be any name you want
<key>CFBundleIconFile</key>
<string>groovy</string>
<key>CFBundleIdentifier</key>
<string>com.apple.groovyConsole</string>
...
```

* original

  ```bash
  <key>CFBundleExecutable</key>
  <string>Application Stub</string>
  <key>CFBundleIconFile</key>
  <string>AutomatorApplet</string>
  <key>CFBundleIdentifier</key>
  <string>com.apple.automator.groovyConsole</string>
  ```

### create script to open the groovyConsole

```bash
$ touch groovyConsole.app/Contents/MacOS/groovyConsole

$ cat > groovyConsole.app/Contents/MacOS/groovyConsole << EOF
  -> #!/bin/bash
  -> /Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/bin/java \\
  ->         -Xdock:name=GroovyConsole \\
  ->         -Xdock:icon=/usr/local/opt/groovy/libexec/lib/groovy.icns \\
  ->         -Dgroovy.jaxb=jaxb \\
  ->         -classpath /usr/local/opt/groovy/libexec/lib/groovy-3.0.6.jar \\
  ->         -Dscript.name=/usr/local/opt/groovy/libexec/bin/groovyConsole \\
  ->         -Dprogram.name=groovyConsole \\
  ->         -Dgroovy.starter.conf=/usr/local/opt/groovy/libexec/conf/groovy-starter.conf \\
  ->         -Dgroovy.home=/usr/local/opt/groovy/libexec \\
  ->         -Dtools.jar=/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/lib/tools.jar org.codehaus.groovy.tools.GroovyStarter \\
  ->         --main groovy.console.ui.Console \\
  ->         --conf /usr/local/opt/groovy/libexec/conf/groovy-starter.conf \\
  ->         --classpath .:/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/lib/tools.jar:/Library/Java/JavaVirtualMachines/jdk1.8.0_211.jdk/Contents/Home/lib/dt.jar:/usr/local/opt/groovy/libexec/lib:.
  -> EOF

$ chmod +x groovyConsole.app/Contents/MacOS/groovyConsole
```

* try validate via execute `groovyConsole.app/Contents/MacOS/groovyConsole` directly. to see whether if the groovyConsole will be opened.

  ![Automator.app &#xBB; show in Alfred](../.gitbook/assets/runable-app-4.png)

### set the icon for new app

> optional

```bash
$ cp /usr/local/opt/groovy/libexec/lib/groovy.icns groovyConsole.app/Contents/Resources
```

* or

  ```bash
  $ ln -sf /usr/local/opt/groovy/libexec/lib/groovy.icns groovyConsole.app/Contents/Resources/groovy.icns
  ```

### move `groovyConsole.app` to `/Application`

```bash
$ mv groovyConsole.app/ /Applications/
```

## [add snippets for input](https://sspai.com/post/36203)

### enable Technical Symbols

* Input Method ⇢ **Show emoji and symbols** ![show emoji &amp; symbols](../.gitbook/assets/snippets-0.png)
* Open **Customized List** ⇢ **Technical Symbols** ![customized list](../.gitbook/assets/snippets-1.png)

  ![technical symbols](../.gitbook/assets/snippets-2.png)

### And snippets

* go to **System Preferences** ⇢ **Keyboard** ⇢ **Test**
* Add snippets as below

  ![snippets](../.gitbook/assets/snippets-3.png)

### finally

![test-1](../.gitbook/assets/snippets-4.png) ![test-2](../.gitbook/assets/snippets-5.png)

## others

### shutdown mac via commands

```bash
$ osascript -e 'tell app 'loginwindow' to «event aevtrsdn»'
```

### [turn off the screen without sleeping](https://apple.stackexchange.com/a/266103/254265)

```bash
$ pmset displaysleepnow
```

* sleep

  ```bash
  $ pmset sleepnow
  ```

* lock

  ```bash
  $ pmset lock
  ```

### launch apps

```bash
$ launchctl list
```

### [extra pkg](https://apple.stackexchange.com/a/309591/254265)

```bash
$ xar -xvf foo.pkg
```

### create image

* create dmg image

  ```bash
  $ hdiutil create -volname "Volume Name" \
                   -srcfolder /path/to/folder \
                   -ov diskimage.dmg
  ```

* create encrypted image

  ```bash
  $ hdiutil create -encryption \
                   -stdinpass \
                   -volname "Volume Name" \
                   -srcfolder /path/to/folder \
                   -ov encrypted.dmg
  ```

* creaste dvd \(for .iso, .img, .dmg\)

  ```bash
  $ hdiutil burn /path/to/image_file
  ```

#### create disk image from volume

```bash
$ sudo hdiutil create ~/Desktop/<name>.dmg -srcdevice /dev/<disk-identifier>
```

* i.e.:

  ```bash
  $ sudo hdiutil create ~/Desktop/Lion.dmg -srcdevice /dev/disk2s4
  ```

#### create disk image from a folder

```bash
$ hdiutil create <imagename>.dmg -volname "<name of volume>" -srcfolder /path/to/folder'
```

* i.e.:

  ```bash
  $ hdiutil create ~/Desktop/marsloTest.dmg -volname 'marslo test' -srcfolder ~/Desktop/marsloTest/
  created: /Users/marslo/Desktop/marsloTest.dmg
  ```

  ![hdiutil create image](../.gitbook/assets/hdiutil-create-image.png)

* setup read & write dmg

  ```bash
  $ hdiutil create ~/Desktop/mTest.dmg \
            -volname "Marslo Test" \
            -srcfolder ~/Desktop/mTest \
            -size 1g \
            -format UDRW
  ```

#### create encrypted disk image

```bash
$ hdiutil create mEncrypted.dmg \
                 -encryption \
                 -size 1g \
                 -volname "mEncrypted Disk Image" \
                 -fs JHFS+ \
                 -srcfolder /path/to/folder \

Enter a new password to secure "mEncrypted.dmg":
Re-enter new password:
....
created: /Users/marslo/Desktop/mEncrypted.dmg
```

![hdiutil create encrypted image](../.gitbook/assets/hdiutil-create-encrypted.png)

#### resize the disk image

```bash
$ hdiutil resize -size <new size> <imagename>.dmg
```

* i.e.:

  ```bash
  $ hdiutil resize -size 2g mEncrypted.dmg
  ```

#### restore disk images

```bash
$ sudo asr restore --source <disk image>.dmg --target /Volumes/<volume name>
```

### disk

{% hint style="info" %}
> reference:
>
> * [Disk Management From the Command-Line, Part 1](http://www.theinstructional.com/guides/disk-management-from-the-command-line-part-1)
> * [Disk Management From the Command-Line, Part 2](http://www.theinstructional.com/guides/disk-management-from-the-command-line-part-2)
> * [Disk Management From the Command-Line, Part 3](http://www.theinstructional.com/guides/disk-management-from-the-command-line-part-3)
{% endhint %}

#### check volumn info

```bash
$ diskutil info <path/to/volumn>
```

* i.e.:

  ```bash
  $ diskutil info /Volumes/iMarsloOSX/
     Device Identifier:         disk1s5
     Device Node:               /dev/disk1s5
     Whole:                     No
     Part of Whole:             disk1

     Volume Name:               iMarsloOSX
     Mounted:                   Yes
     Mount Point:               /
  ```

* list disks and volumns

  ```bash
  $ diskutil list
  ```

  or

  ```bash
  $ diskutil list disk1
  ```

  * or [lsblk](https://command-not-found.com/lsblk)

    ```bash
    $ docker run cmd.cat/lsblk lsblk
    NAME   MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
    vda    254:0    0  16G  0 disk
    └─vda1 254:1    0  16G  0 part /etc/hosts
    ```

  * or [lshw](https://command-not-found.com/lshw)

    ```bash
    $ docker run cmd.cat/lshw lshw -class disk
      *-virtio1
           description: Virtual I/O device
           physical id: 0
           bus info: virtio@1
           logical name: vda
           configuration: driver=virtio_blk
    ```

#### list the apfs info

```bash
$ diskutil apfs list
APFS Container (1 found)
|
+-- Container disk1 ********-****-****-****-************
    ====================================================
    APFS Container Reference:     disk1
    Size (Capacity Ceiling):      250685575168 B (250.7 GB)
    Capacity In Use By Volumes:   176258826240 B (176.3 GB) (70.3% used)
    Capacity Not Allocated:       74426748928 B (74.4 GB) (29.7% free)
    |
    +-< Physical Store...>
    |
    +-> ...
```

#### check detail diskage usage

```bash
$ sudo fs_usage
21:03:47  ioctl        0.000003   iTerm2
21:03:47  ioctl        0.000003   iTerm2
21:03:47  close        0.000031   privoxy
21:03:47  select       0.000004   privoxy
...
```

#### erase disk

{% hint style="info" %}
| File System | Abbreviation |
| :--- | :---: |
| Mac OS Extended \(Journaled\) | `JHFS+` |
| Mac OS Extended | `HFS+` |
| MS-DOS fat32 | `FAT32` |
| ExFAT | `ExFAT` |

```bash
$ diskutil listFilesystems
...
-------------------------------------------------------------------------------
PERSONALITY                     USER VISIBLE NAME
-------------------------------------------------------------------------------
Case-sensitive APFS             APFS (Case-sensitive)
  (or) APFSX
APFS                            APFS
  (or) APFSI
ExFAT                           ExFAT
Free Space                      Free Space
  (or) FREE
MS-DOS                          MS-DOS (FAT)
MS-DOS FAT12                    MS-DOS (FAT12)
MS-DOS FAT16                    MS-DOS (FAT16)
MS-DOS FAT32                    MS-DOS (FAT32)
  (or) FAT32
HFS+                            Mac OS Extended
Case-sensitive HFS+             Mac OS Extended (Case-sensitive)
  (or) HFSX
Case-sensitive Journaled HFS+   Mac OS Extended (Case-sensitive, Journaled)
  (or) JHFSX
Journaled HFS+                  Mac OS Extended (Journaled)
  (or) JHFS+
UFSD_NTFS                       Microsoft NTFS
```
{% endhint %}

* ExFAT

  ```bash
  $ diskutil eraseDisk ExFAT iMarsloUSB /dev/disk2
  Started erase on disk2
  Unmounting disk
  Creating the partition map
  Waiting for partitions to activate
  Formatting disk2s2 as ExFAT with name iMarsloUSB
  Volume name      : iMarsloUSB
  Partition offset : 411648 sectors (210763776 bytes)
  Volume size      : 246534144 sectors (126225481728 bytes)
  Bytes per sector : 512
  Bytes per cluster: 131072
  FAT offset       : 2048 sectors (1048576 bytes)
  # FAT sectors    : 8192
  Number of FATs   : 1
  Cluster offset   : 10240 sectors (5242880 bytes)
  # Clusters       : 962984
  Volume Serial #  : 5ff81490
  Bitmap start     : 2
  Bitmap file size : 120373
  Upcase start     : 3
  Upcase file size : 5836
  Root start       : 4
  Mounting disk
  Finished erase on disk2
  ```

  * check

    ```bash
    $ diskutil info disk2s1
       Device Identifier:         disk2s1
       Device Node:               /dev/disk2s1
       Whole:                     No
       Part of Whole:             disk2

       Volume Name:               EFI
       Mounted:                   No

       Partition Type:            EFI
       File System Personality:   MS-DOS FAT32
       Type (Bundle):             msdos
       Name (User Visible):       MS-DOS (FAT32)
       ...
       ...

    $ diskutil info disk2s2
       Device Identifier:         disk2s2
       Device Node:               /dev/disk2s2
       Whole:                     No
       Part of Whole:             disk2

       Volume Name:               iMarsloUSB
       Mounted:                   Yes
       Mount Point:               /Volumes/iMarsloUSB

       Partition Type:            Microsoft Basic Data
       File System Personality:   ExFAT
       Type (Bundle):             exfat
       Name (User Visible):       ExFAT
       ...
       ...
    ```

**Verifying and Repairing Volumes**

```bash
$ diskutil verifyVolume /Volumes/<volume name>
$ diskutil repairVolume /Volumes/<volume name>
```

#### rename volume

```bash
$ diskutil rename "<current name of volume>" "<new name>"
```

#### Partitioning a Disk

{% hint style="info" %}
> reference:
>
> * `GPT`: GUID Partition Table
> * `APM`: Apple Partition Map
> * `MBR`: Master Boot Records
{% endhint %}

```bash
$ diskutil partitionDisk /dev/disk2 GPT JHFS+ New 0b
```

* multiple partitions

  ```bash
  $ diskutil partitionDisk /dev/disk2 GPT \
             JHFS+ First 10g \
             JHFS+ Second 10g \
             JHFS+ Third 10g \
             JHFS+ Fourth 10g \
             JHFS+ Fifth 0b
  ```

* Splitting Partitions

  ```bash
  $ diskutil splitPartition /dev/disk2s6 \
             JHFS+ Test 10GB \
             JHFS+ Test2 0b
  ```

* Merging Partitions

  ```bash
  $ diskutil mergePartitions \
             JHFS+ \
             NewName \
             <first disk identifier in range> \
             <last disk identifier in range>
  ```

  i.e.:

  ```bash
  $ diskutil mergePartitions JHFS+ NewName disk2s4 disk2s6
  ```

#### [check usb](https://apple.stackexchange.com/a/170118/254265)

```bash
$ system_profiler SPUSBDataType
```

* or get xml format

  ```bash
  $ system_profiler -xml SPUSBDataType
  ```

* or

  ```bash
  $ ioreg -p IOUSB
  ```

* or

  ```bash
  $ ioreg -p IOUSB -w0 -l
  ```

  * or get device name

    ```bash
     $ ioreg -p IOUSB -w0 | sed 's/[^o]*o //; s/@.*$//' | grep -v '^Root.*'
    ```

### disable startup music

```bash
$ sudo nvram SystemAudioVolume=" "
```

### 3D lock screen

```bash
$ /System/Library/CoreServices/Menu\ Extras/User.menu/Contents/Resources/CGSession -suspend
```

### take screenshot after 3 sec

```bash
$ screencapture -T 3 -t jpg -P delayedpic.jpg
```

### setup welcome text in login screen

```bash
$ sudo defaults write /Library/Preferences/com.apple.loginwindow LoginwindowText 'Awesome Marslo!!'
```

### show message on desktop

```bash
$ sudo jamf displayMessage -message "Hello World!"
```

### modify font in plist

* original

  ```bash
  $ defaults read ~/Library/Preferences/groovy.console.ui.plist
  {
      "/groovy/console/ui/" =     {
          autoClearOutput = true;
          compilerPhase = 4;
          currentFileChooserDir = "/Users/marslo/Desktop";
          decompiledFontSize = 12;
          fontSize = 18;
          frameHeight = 600;
          frameWidth = 800;
          frameX = 198;
          frameY = 201;
          horizontalSplitterLocation = 100;
          inputAreaHeight = 576;
          inputAreaWidth = 1622;
          outputAreaHeight = 354;
          outputAreaWidth = 1676;
          showClosureClasses = false;
          showIndyBytecode = false;
          showScriptClass = true;
          showScriptFreeForm = false;
          showScriptInOutput = false;
          showTreeView = true;
          threadInterrupt = true;
          verticalSplitterLocation = 100;
      };
  }
  ```

  * [or](https://stackoverflow.com/a/56238780/2940319)

    ```bash
    $ /usr/libexec/PlistBuddy -c 'print ":/groovy/console/ui/:fontSize"' ~/Library/Preferences/groovy.console.ui.plist
    18
    ```

* change

  ```bash
  $ /usr/libexec/PlistBuddy -c 'Set ":/groovy/console/ui/:fontSize" 24' ~/Library/Preferences/groovy.console.ui.plist
  $ /usr/libexec/PlistBuddy -c 'Print ":/groovy/console/ui/:fontSize"' ~/Library/Preferences/groovy.console.ui.plist
  24
  ```

### show process details

![activity monitor](../.gitbook/assets/activity-monitor.png)
