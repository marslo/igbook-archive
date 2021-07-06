# havefun

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [I'm very busy](havefun.md#im-very-busy)
* [Press Any Key to Continue](havefun.md#press-any-key-to-continue)
* [Simulate type mechine \[Pretty Cool!!\]](havefun.md#simulate-type-mechine-pretty-cool)
* [Get how many days left this years](havefun.md#get-how-many-days-left-this-years)
* [Get week number](havefun.md#get-week-number)
* [DOS tree](havefun.md#dos-tree)
* [Set Volume by command](havefun.md#set-volume-by-command)
* [cat and tac](havefun.md#cat-and-tac)
* [ASCII chart](havefun.md#ascii-chart)
* [Char chart](havefun.md#char-chart)
* [Hate someone](havefun.md#hate-someone)
* [Star war](havefun.md#star-war)

## I'm very busy

```text
$ cat /dev/urandom | hexdump -C | grep "ca fe"
```

## Press Any Key to Continue

```text
$ read -sn 1 -p "Press any key to continue..." && echo "\n"
Press any key to continue...\n
```

## Simulate type mechine \[Pretty Cool!!\]

```bash
$ sudo apt-get intall pv
$ echo "Very very very very very long words" | pv -qL $[10+(-2 + RANDOM%5)]

# or
$ sudo apt-get install randtype
$ echo "Very very very very very long words" | randtype -m 4
```

## Get how many days left this years

```text
$ echo "There are $(($(date +%j -d"Dec 31, $(date +%Y)")-$(date +%j))) left in year $(date +%Y)."
There are 323 left in year 2014.
```

## Get week number

```text
$ date +"%V"
08
```

## DOS tree

```text
$ find . -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'
.
|____a_b
|____b_a
```

## Set Volume by command

```text
$ pacmd set-sink-volume 0 0x10000
Welcome to PulseAudio! Use "help" for usage information.
```

## cat and tac

```text
$ cat a_b
1
2
3
$ tac a_b
3
2
1
```

## ASCII chart

```text
$ figlet Marslo
 __  __                _
|  \/  | __ _ _ __ ___| | ___
| |\/| |/ _` | '__/ __| |/ _ \
| |  | | (_| | |  \__ \ | (_) |
|_|  |_|\__,_|_|  |___/_|\___/
```

## Char chart

```text
$ toilet marslo
                             ""#
 mmmmm   mmm    m mm   mmm     #     mmm
 # # #  "   #   #"  " #   "    #    #" "#
 # # #  m"""#   #      """m    #    #   #
 # # #  "mm"#   #     "mmm"    "mm  "#m#"
```

## Hate someone

```text
┌─ (marslo@MarsloJiao ~) ->
└─ $ :(){ :|: &  };:
```

## Star war

```text
┌─ (marslo@MarsloJiao ~) ->
└─ $ telnet towel.blinkenlights.nl
```

