# windows

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [move between windws](windows.md#move-between-windws)
* [resize](windows.md#resize)
  * [horizontal resize](windows.md#horizontal-resize)
  * [vertical resize](windows.md#vertical-resize)
* [quickfix](windows.md#quickfix)

{% hint style="info" %}
> reference:
>
> * [windows.txt](https://vimhelp.org/windows.txt.html)
{% endhint %}

## move between windws

| commands | shortcut |
| :---: | :---: |
| `:wincmd l` | ctrl + w ⇢ l |
| `:wincmd h` | ctrl + w ⇢ h |
| `:wincmd j` | ctrl + w ⇢ j |
| `:wincmd k` | ctrl + w ⇢ k |

## resize

> reference:
>
> * [Resize splits more quickly](https://vim.fandom.com/wiki/Resize_splits_more_quickly)
>
>   maximium window: ctrl + w ⇢ \_

### horizontal resize

> `:res` is the shortcut of `:resize`

| commands or shortcut | comments |
| :--- | :--- |
| `:res n` | setup the width to  lines |
| `:resize -n` | reduce  lines of the width |
| `:resize +n` | extend  lines of the width |
| ctrl + w ⇢ + | extend 1 line |
| `:wincmd +` | extend 1 line |
| ctrl + w ⇢ - | reduce 1 line |
| `:wincmd -` | reduce 1 line |
| ctrl + w ⇢ = | resize to default: `50%` |
| `:wincmd =` | resize to default: `50%` |
| ctrl + w ⇢ \_ | maximum the window |
| `:wincmd _` | maximum the window |

![resize](../../.gitbook/assets/resize.gif)

### vertical resize

| commands or shortcut | comments |
| :--- | :--- |
| `:vertical res n` | setup the width to  columns |
| `:vertical resize -n` | reduce  columns of the width |
| `:vertical resize +n` | extend  columns of the width |
| ctrl + w ⇢ &gt; | extend 1 column |
| `:wincmd >` | extend 1 column |
| ctrl + w ⇢ &lt; | reduce 1 column |
| `:wincmd <` | reduce 1 column |
| ctrl + w ⇢ = | resize to default: `50%` |
| `:wincmd =` | resize to default: `50%` |
| ctrl + w ⇢ \| | maximum the window |
| `:wincmd ⎮` | maximum the window |

![vertical resize](../../.gitbook/assets/resize-vertical.gif)

## [quickfix](http://vimdoc.sourceforge.net/htmldoc/quickfix.html)

![quickfix windows](../../.gitbook/assets/vimgrep-quckfix-window.gif)

* [Automatically fitting a quickfix window height](https://vim.fandom.com/wiki/Automatically_fitting_a_quickfix_window_height)

  ```text
  " .vimrc
  au FileType qf call AdjustWindowHeight(3, 10)
  function! AdjustWindowHeight(minheight, maxheight)
    exe max([min([line("$"), a:maxheight]), a:minheight]) . "wincmd _"
  endfunction
  ```

