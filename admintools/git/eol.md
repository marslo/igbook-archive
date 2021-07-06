# eol

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [theory](eol.md#theory)
  * [list eol in repo](eol.md#list-eol-in-repo)
  * [core.autocrlf](eol.md#coreautocrlf)
  * [please notice](eol.md#please-notice)
* [practice](eol.md#practice)
  * [force using `lf` in both remote and local](eol.md#force-using-lf-in-both-remote-and-local)
  * [ignore `warning: LF will be replaced by CRLF`](eol.md#ignore-warning-lf-will-be-replaced-by-crlf)
* [Reference](eol.md#reference)

## theory

### [list eol in repo](https://stackoverflow.com/a/21822812/2940319)

```bash
> git ls-files --eol
```

### core.autocrlf

#### [parameters](https://stackoverflow.com/a/41282375/2940319)

| core.autocrlf | false | input | true |
| :---: | :---: | :---: | :---: |
| git commit | `lf > lf`  `cr > cr`   `crlf > crlf` | `lf > lf`   `cr > cr`   `crlf > lf` | `lf > lf`   `cr > cr`   `crlf > lf` |
| git checkout | `lf > lf`  `cr > cr`   `crlf > crlf` | `lf > lf`   `cr > cr`   `crlf > crlf` | `lf > lf`   `cr > cr`   `crlf > crlf` |

[normally, it will looks like](https://stackoverflow.com/a/20653073/2940319)

```bash
core.autocrlf=true:      core.autocrlf=input:     core.autocrlf=false:

        repo                     repo                     repo
      ^      V                 ^      V                 ^      V
     /        \               /        \               /        \
crlf->lf    lf->crlf     crlf->lf       \             /          \
   /            \           /            \           /            \
```

#### set in GUI

![git line ending setup](../../.gitbook/assets/git-eol.png)

* checkout Windows-style, commit Unix-style line endings:

  ```bash
  $ git config --global core.autocrlf true
  ```

  * Text files checked-out from the repository that have only `LF` characters are normalized to CRLF in your working tree; files that contain `CRLF` in the repository will not be touched
  * Text files that have only `LF` characters in the repository, are normalized from CRLF to LF when committed back to the repository. Files that contain CRLF in the repository will be committed untouched.

* Checkout as-is, commit Unix-Style line endings:

  ```bash
  $ git config --global core.autocrlf input
  ```

  * Text files checked-out from the repository will keep original `EOL` characters in your working tree.
  * Text files in your working tree with `CRLF`characters are normalized to `LF` when committed back to the repository.

* Checkout as-is, commit as-is:

  ```bash
  $ git config --global core.autocrlf false
  ```

  * `core.eol` dictates `EOL` characters in the text files of your working tree.
  * `core.eol = native` by default, which means Windows `EOLs` are `CRLF` and \*nix `EOLs` are `LF` in working trees.
  * Repository gitattributes settings determines `EOL` character normalization for commits to the repository \(default is normalization to `LF` characters\).

### [please notice](https://git-scm.com/docs/gitattributes#gitattributes-Settostringvalueauto)

> `eol`
>
> This attribute sets a specific line-ending style to be used in the working directory. It enables end-of-line conversion without any content checks, effectively setting the text attribute. Note that setting this attribute on paths which are in the index with CRLF line endings may make the paths to be considered dirty. Adding the path to the index again will normalize the line endings in the index.

## practice

### force using `lf` in both remote and local

```bash
$ git config core.eol lf
$ git config core.autocrlf input
```

or

```bash
$ git config --global core.eol lf
$ git config --global core.autocrlf input
```

### [ignore `warning: LF will be replaced by CRLF`](https://stackoverflow.com/a/17628353/2940319)

```bash
$ git config --global core.safecrlf false
```

## Reference

* [Force LF eol in git repo and working copy](https://stackoverflow.com/a/9977954/2940319)

