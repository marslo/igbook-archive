<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [I'm very busy](#im-very-busy)
- [Press Any Key to Continue](#press-any-key-to-continue)
- [Simulate type mechine [Pretty Cool!!]](#simulate-type-mechine-pretty-cool)
- [Get how many days left this years](#get-how-many-days-left-this-years)
- [Get week number](#get-week-number)
- [DOS tree](#dos-tree)
- [Set Volume by command](#set-volume-by-command)
- [cat and tac](#cat-and-tac)
- [ASCII chart](#ascii-chart)
- [Char chart](#char-chart)
- [Hate someone](#hate-someone)
- [Star war](#star-war)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

### I'm very busy
    [marslo@MJ ~/GoodNote]
    $ cat /dev/urandom | hexdump -C | grep "ca fe"

### Press Any Key to Continue
    [marslo@MJ ~]
    $ read -sn 1 -p "Press any key to continue..." && echo "\n"
    Press any key to continue...\n

### Simulate type mechine [Pretty Cool!!]
    [marslo@MJ ~]
    $ sudo apt-get intall pv
    [marslo@MJ ~]
    $ echo "Very very very very very long words" | pv -qL $[10+(-2 + RANDOM%5)]

    OR
    [marslo@MJ ~/GoodNote]
    $ sudo apt-get install randtype
    [marslo@MJ ~/GoodNote]
    $ echo "Very very very very very long words" | randtype -m 4

### Get how many days left this years
    [marslo@MJ ~/GoodNote]
    $ echo "There are $(($(date +%j -d"Dec 31, $(date +%Y)")-$(date +%j))) left in year $(date +%Y)."
    There are 323 left in year 2014.

### Get week number
    [marslo@MJ ~/GoodNote]
    $ date +"%V"
    08

### DOS tree
    [marslo@MJ ~/GoodNote]
    $ find . -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'
    .
    |____a_b
    |____b_a

### Set Volume by command
    [marslo@MJ ~/GoodNote]
    $ pacmd set-sink-volume 0 0x10000
    Welcome to PulseAudio! Use "help" for usage information.

### cat and tac
    [marslo@MJ ~/GoodNote]
    $ cat a_b
    1
    2
    3
    [marslo@MJ ~/GoodNote]
    $ tac a_b
    3
    2
    1

### ASCII chart
    [marslo@MJ ~]
    $ figlet Marslo
     __  __                _
    |  \/  | __ _ _ __ ___| | ___
    | |\/| |/ _` | '__/ __| |/ _ \
    | |  | | (_| | |  \__ \ | (_) |
    |_|  |_|\__,_|_|  |___/_|\___/

### Char chart
    [marslo@MJ ~/Tools/Git/MyNotes/GoodCommand]
    $ toilet marslo
                                 ""#
     mmmmm   mmm    m mm   mmm     #     mmm
     # # #  "   #   #"  " #   "    #    #" "#
     # # #  m"""#   #      """m    #    #   #
     # # #  "mm"#   #     "mmm"    "mm  "#m#"

### Hate someone
    ┌─ (marslo@MarsloJiao ~) ->
    └─ $ :(){ :|: &  };:

### Star war
    ┌─ (marslo@MarsloJiao ~) ->
    └─ $ telnet towel.blinkenlights.nl
