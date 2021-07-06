# tricky

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [save & restore screen](tricky.md#save--restore-screen)
  * [`tput`](tricky.md#tput)
  * [`echo`](tricky.md#echo)
* [Terminfo escape sequences](tricky.md#terminfo-escape-sequences)
* [others](tricky.md#others)
  * [clear screen](tricky.md#clear-screen)
  * [show TERM](tricky.md#show-term)
  * [show terminal width](tricky.md#show-terminal-width)
  * [customized colorful output](tricky.md#customized-colorful-output)

{% hint style="info" %}
> reference
>
> * [Terminal codes \(ANSI/VT100\) introduction](https://wiki.bash-hackers.org/scripting/terminalcodes)
{% endhint %}

## save & restore screen

### `tput`

* clear

  ```bash
  $ tput smcup
  ```

* restore

  ```bash
  $ tput rmcup
  ```

### `echo`

* save

  ```bash
  $ echo -e '\033[?47h'
  ```

* restore

  ```bash
  $ echo -e '\033[?47l'
  ```

## Terminfo escape sequences

```bash
$ infocmp
  ...
  colors#256, cols#80, it#8, lines#24, pairs#32767,
  bel=^G, blink=\E[5m, bold=\E[1m, cbt=\E[Z, civis=\E[?25l,
  clear=\E[H\E[2J, cnorm=\E[?12l\E[?25h, cr=^M,
  ...
```

## others

### clear screen

```bash
$ tput home
```

### show TERM

```bash
$ tput color
```

### show terminal width

```bash
$ tput cols
```

### [customized colorful output](https://unix.stackexchange.com/a/163781/29178)

```bash
$ export GREP_COLORS="sl=0;33;49:ms=1;34;49"
$ find /etc/ -type f | head | grep --color=always '^\|[^/]*$'
```

![customized color output](../../.gitbook/assets/colorful-tricky.png)

