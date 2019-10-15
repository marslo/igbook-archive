## download xcode from commandline
* get cookies.txt
    * install google chrome extension from [official website](https://chrome.google.com/webstore/detail/cookiestxt/njabckikapfpffapmjgojcnbfjonfjfg?hl=en)
    * login [developer.apple.com](https://developer.apple.com/download/more/)
    * select cookies.txt and download
    ![download cookies.txt](../../screenshot/cookies.txt-1.png)

* get xcode download url
    * right click and select **Copy Link Address**
    ![download cookies.txt](../../screenshot/cookies.txt-2.png)

* download xcode
    ```bash
    $ wget --cookies=on \
           --load-cookies=cookies.txt \
           --keep-session-cookies \
           --save-cookies=cookies.txt \
           https://developer.apple.com/services-account/download?path=/Developer_Tools/Xcode_11.2_beta_2/Xcode_11.2_beta_2.xip
    ```
### Appendix
* xcode 11
    | Xcode 11.2beta 2                        | https://download.developer.apple.com/Developer_Tools/Xcode_11.2_beta_2/Xcode_11.2_beta_2.xip                                               |
    | Command Line Tools for Xcode 11.2beta 2 | https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_for_Xcode_11.2_beta_2/Command_Line_Tools_for_Xcode_11.2_beta_2.dmg |
    | Xcode 11.1                              | https://download.developer.apple.com/Developer_Tools/Xcode_11.1/Xcode_11.1.xip                                                             |
    | Command Line Tools for Xcode 11.2beta   | https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_for_Xcode_11.2_beta/Command_Line_Tools_for_Xcode_11.2_beta.dmg     |
    | Xcode 11.2beta                          | https://download.developer.apple.com/Developer_Tools/Xcode_11.2_beta/Xcode_11.2_beta.xip                                                   |
    | Xcode 11                                | https://download.developer.apple.com/Developer_Tools/Xcode_11/Xcode_11.xip                                                                 |
    | Command Line Tools for Xcode 11         | https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_for_Xcode_11/Command_Line_Tools_for_Xcode_11.dmg                   |
    | Additional Tools for Xcode 11           | https://download.developer.apple.com/Developer_Tools/Additional_Tools_for_Xcode_11/Additional_Tools_for_Xcode_11.dmg                       |

* xcode 10
    | Xcode 10.3                                        | https://download.developer.apple.com/Developer_Tools/Xcode_10.3/Xcode_10.3.xip                                                                               |
    | Command Line Tools (macOS 10.14) for Xcode 10.3   | https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_macOS_10.14_for_Xcode_10.3/Command_Line_Tools_macOS_10.14_for_Xcode_10.3.dmg         |
    | Xcode 10.2.1                                      | https://download.developer.apple.com/Developer_Tools/Xcode_10.2.1/Xcode_10.2.1.xip                                                                           |
    | Command Line Tools (macOS 10.14) for Xcode 10.2.1 | https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_macOS_10.14_for_Xcode_10.2.1.dmg/Command_Line_Tools_macOS_10.14_for_Xcode_10.2.1.dmg |
    | Xcode 10.2                                        | https://download.developer.apple.com/Developer_Tools/Xcode_10.2/Xcode_10.2.xip                                                                               |
    | Command Line Tools (macOS 10.14) for Xcode 10.2   | https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_macOS_10.14_for_Xcode_10.2/Command_Line_Tools_macOS_10.14_for_Xcode_10.2.dmg         |
    | Additional Tools for Xcode 10.2                   | https://download.developer.apple.com/Developer_Tools/Xcode_10.2/Xcode_10.2.xip                                                                               |
    | Xcode 10.1                                        | https://download.developer.apple.com/Developer_Tools/Xcode_10.1/Xcode_10.1.xip                                                                               |
    | Additional Tools for Xcode 10.1                   | https://download.developer.apple.com/Developer_Tools/Additional_Tools_for_Xcode_10.1/Additional_Tools_for_Xcode_10.1.dmg                                     |
    | Command Line Tools (macOS 10.14) for Xcode 10.1   | https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_macOS_10.14_for_Xcode_10.1/Command_Line_Tools_macOS_10.14_for_Xcode_10.1.dmg         |
    | Command Line Tools (macOS 10.13) for Xcode 10.1   | https://download.developer.apple.com/Developer_Tools/Command_Line_Tools_macOS_10.13_for_Xcode_10.1/Command_Line_Tools_macOS_10.13_for_Xcode_10.1.dmg         |
