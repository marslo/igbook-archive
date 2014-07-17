- I'm very busy
    <pre><code>[marslo@MJ ~/GoodNote]
    $ cat /dev/urandom | hexdump -C | grep "ca fe"
    </code></pre>

- Press Any Key to Continue
    <pre><code>[marslo@MJ ~]
    $ read -sn 1 -p "Press any key to continue..." && echo "\n"
    Press any key to continue...\n
    </code></pre>

- Simulate type mechine [Pretty Cool!!]
    <pre><code>[marslo@MJ ~]
    $ sudo apt-get intall pv
    [marslo@MJ ~]
    $ echo "Very very very very very long words" | pv -qL $[10+(-2 + RANDOM%5)]
    </code></pre>
    OR
    <pre><code>[marslo@MJ ~/GoodNote]
    $ sudo apt-get install randtype
    [marslo@MJ ~/GoodNote]
    $ echo "Very very very very very long words" | randtype -m 4
    </code></pre>

- Get how many days left this years
    <pre><code>[marslo@MJ ~/GoodNote]
    $ echo "There are $(($(date +%j -d"Dec 31, $(date +%Y)")-$(date +%j))) left in year $(date +%Y)."
    There are 323 left in year 2014.
    </code></pre>

- Get week number
    <pre><code>[marslo@MJ ~/GoodNote]
    $ date +"%V"
    08
    </code></pre>

- DOS tree
    <pre><code>[marslo@MJ ~/GoodNote]
    $ find . -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'
    .
    |____a_b
    |____b_a
    </code></pre>

- Set Volume by command
    <pre><code>[marslo@MJ ~/GoodNote]
    $ pacmd set-sink-volume 0 0x10000
    Welcome to PulseAudio! Use "help" for usage information.
    </code></pre>

- cat and tac
    <pre><code>[marslo@MJ ~/GoodNote]
    $ cat a_b
    1
    2
    3
    [marslo@MJ ~/GoodNote]
    $ tac a_b
    3
    2
    1
    </code></pre>

- ASCII chart
    <pre><code>[marslo@MJ ~]
    $ figlet Marslo
     __  __                _
    |  \/  | __ _ _ __ ___| | ___
    | |\/| |/ _` | '__/ __| |/ _ \
    | |  | | (_| | |  \__ \ | (_) |
    |_|  |_|\__,_|_|  |___/_|\___/
    </code></pre>

- Char chart
    <pre><code>[marslo@MJ ~/Tools/Git/MyNotes/GoodCommand]
    $ toilet marslo
                                 ""#
     mmmmm   mmm    m mm   mmm     #     mmm
     # # #  "   #   #"  " #   "    #    #" "#
     # # #  m"""#   #      """m    #    #   #
     # # #  "mm"#   #     "mmm"    "mm  "#m#"
    </code></pre>

- Hate someone
    <pre><code>┌─ (marslo@MarsloJiao ~) ->
    └─ $ :(){ :|: &  };:
    </code></pre>

- Star war
    <pre><code>┌─ (marslo@MarsloJiao ~) ->
    └─ $ telnet towel.blinkenlights.nl
    </code></pre>
