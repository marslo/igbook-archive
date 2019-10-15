## download xcode from commandline
* get cookies.txt
    * install google chrome extension from [official website](https://chrome.google.com/webstore/detail/cookiestxt/njabckikapfpffapmjgojcnbfjonfjfg?hl=en)
    * login [developer.apple.com](https://developer.apple.com/download/more/)
    * select cookies.txt and download
    ![download cookies.txt](../../screenshot/cookies.txt-1.png)

* get xcode download url
    * right click and select **Copy Link Address**
    ![download cookies.txt](../../screenshot/cookies.txt-2.png)

* download xcode (inspired from [here](https://stackoverflow.com/a/4089758/2940319) and [here](https://stackoverflow.com/a/46020878/2940319))
    ```bash
    $ wget --cookies=on \
           --load-cookies=cookies.txt \
           --keep-session-cookies \
           --save-cookies=cookies.txt \
           https://download.developer.apple.com/Developer_Tools/Xcode_11.2_beta_2/Xcode_11.2_beta_2.xip
    ```
    * exmaple
    ```bash
    $ wget --cookies=on \
    >          --load-cookies=cookies.txt \
    >          --keep-session-cookies \
    >          --save-cookies=cookies.txt \
    >          https://download.developer.apple.com/Developer_Tools/Xcode_11.2_beta_2/Xcode_11.2_beta_2.xip
    --2019-10-15 07:55:18--  https://download.developer.apple.com/Developer_Tools/Xcode_11.2_beta_2/Xcode_11.2_beta_2.xip
    Resolving download.developer.apple.com (download.developer.apple.com)... 17.253.17.207, 17.253.17.211
    Connecting to download.developer.apple.com (download.developer.apple.com)|17.253.17.207|:443... connected.
    HTTP request sent, awaiting response... 200 OK
    Length: 7805079698 (7.3G) [application/octet-stream]
    Saving to: ‘Xcode_11.2_beta_2.xip’

    100%[===========================================================================================================>] 7,805,079,698  112MB/s   in 70s

    2019-10-15 07:53:07 (106 MB/s) - ‘Xcode_11.2_beta_2.xip’ saved [7805079698/7805079698]

    $ ls -altrh Xcode_11.2_beta_2.xip
    -rw-rw-r-- 1 devops devops 7.3G Oct  9 13:27 Xcode_11.2_beta_2.xip
    ```

### Appendix

|            xcode |                                                                                                                                                                                                                                                                            url                                                                                                                                                                                                                                                                           |
|-----------------:|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| Xcode 11.2beta 2 |                                                                                                                                                 ```https://download.developer.apple.com/Developer_Tools/Xcode_11.2_beta_2/Xcode_11.2_beta_2.xip``` <br> ```https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_for_Xcode_11.2_beta_2/Command_Line_Tools_for_Xcode_11.2_beta_2.dmg```                                                                                                                                                 |
|       Xcode 11.1 |                                                                                                                                                          ```https://download.developer.apple.com/Developer_Tools/Xcode_11.1/Xcode_11.1.xip``` <br> ```https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_for_Xcode_11.2_beta/Command_Line_Tools_for_Xcode_11.2_beta.dmg```                                                                                                                                                          |
|   Xcode 11.2beta |                                                                                                                                                                                                                              ```https://download.developer.apple.com/Developer_Tools/Xcode_11.2_beta/Xcode_11.2_beta.xip```                                                                                                                                                                                                                              |
|         Xcode 11 |                                                                                                   ```https://download.developer.apple.com/Developer_Tools/Xcode_11/Xcode_11.xip``` <br> ```https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_for_Xcode_11/Command_Line_Tools_for_Xcode_11.dmg``` <br> ```https://download.developer.apple.com/Developer_Tools/Additional_Tools_for_Xcode_11/Additional_Tools_for_Xcode_11.dmg```                                                                                                   |
|       Xcode 10.3 |                                                                                                                                                    ```https://download.developer.apple.com/Developer_Tools/Xcode_10.3/Xcode_10.3.xip```<br> ```https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_macOS_10.14_for_Xcode_10.3/Command_Line_Tools_macOS_10.14_for_Xcode_10.3.dmg```                                                                                                                                                   |
|     Xcode 10.2.1 |                                                                                                                                              ```https://download.developer.apple.com/Developer_Tools/Xcode_10.2.1/Xcode_10.2.1.xip```<br> ```https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_macOS_10.14_for_Xcode_10.2.1.dmg/Command_Line_Tools_macOS_10.14_for_Xcode_10.2.1.dmg```                                                                                                                                             |
|       Xcode 10.2 |                                                                                                      ```https://download.developer.apple.com/Developer_Tools/Xcode_10.2/Xcode_10.2.xip```<br> ```https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_macOS_10.14_for_Xcode_10.2/Command_Line_Tools_macOS_10.14_for_Xcode_10.2.dmg```   <br> ```https://download.developer.apple.com/Developer_Tools/Xcode_10.2/Xcode_10.2.xip```                                                                                                     |
|       Xcode 10.1 | ```https://download.developer.apple.com/Developer_Tools/Xcode_10.1/Xcode_10.1.xip``` <br> ```https://download.developer.apple.com/Developer_Tools/Additional_Tools_for_Xcode_10.1/Additional_Tools_for_Xcode_10.1.dmg``` <br> ```https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_macOS_10.14_for_Xcode_10.1/Command_Line_Tools_macOS_10.14_for_Xcode_10.1.dmg``` <br> ```https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_macOS_10.13_for_Xcode_10.1/Command_Line_Tools_macOS_10.13_for_Xcode_10.1.dmg``` |

* [additional info](https://stackoverflow.com/a/44390183/2940319)
