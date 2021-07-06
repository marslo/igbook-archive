# vim

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [check where vim executable package](./#check-where-vim-executable-package)
* [tricky](./#tricky)
* [Capitalize words and regions easily](./#capitalize-words-and-regions-easily)
* [Switching case of characters](./#switching-case-of-characters)

## check where vim executable package

```text
:echo v:progpath
```

[or](https://stackoverflow.com/a/48858718/2940319)

```text
  :echo $VIM
```

## tricky

* List startup script files

  ```text
  :scriptnames
  ```

* [check customized completion](https://github.com/xavierd/clang_complete/issues/452#issuecomment-139872204)

  ```text
  :set completefunc?
  completefunc=youcompleteme#CompleteFunc
  ```

* show terminal type

  ```text
  :TERM_PROGRAM
  iTerm.app
  ```

* [filetype in vim language](https://stackoverflow.com/a/63255521/2940319)

  ```text
  if index(['vim', 'c', 'cpp'], &filetype) != -1
    echom "hello!"
  endif
  ```

  [or](https://stackoverflow.com/a/29407473/2940319)

  ```text
  let fts = ['c', 'cpp']
  if index(fts, &filetype) == -1
    " do stuff
  endif
  ```

## [Capitalize words and regions easily](https://vim.fandom.com/wiki/Capitalize_words_and_regions_easily)

| shortcut | comments |
| :---: | :--- |
| `gcw` | capitalize word \(from cursor position to end of word\) |
| `gcW` | capitalize WORD \(from cursor position to end of WORD\) |
| `gciw` | capitalize inner word \(from start to end\) |
| `gciW` | capitalize inner WORD \(from start to end\) |
| `gcis` | capitalize inner sentence |
| `gc$` | capitalize until end of line \(from cursor postition\) |
| `gcgc` | capitalize whole line \(from start to end\) |
| `gcc` | capitalize whole line |
| `{Visual}gc` | capitalize highlighted text |

## [Switching case of characters](https://vim.fandom.com/wiki/Switching_case_of_characters)

* lowercase all

  ```text
  gu
  ```

* uppercase all

  ```text
  gU
  ```

* reverse all

  ```text
  g~
  ```

