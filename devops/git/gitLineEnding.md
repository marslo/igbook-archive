### core.autocrlf

| core.autocrlf |                    false                   |                    input                    |                     true                    |
|:-------------:|:------------------------------------------:|:-------------------------------------------:|:-------------------------------------------:|
|   git commit  | `lf > lf` <br>`cr > cr` <br> `crlf > crlf` |  `lf > lf` <br> `cr > cr` <br> `crlf > lf`  |  `lf > lf` <br> `cr > cr` <br> `crlf > lf`  |
|  git checkout | `lf > lf` <br>`cr > cr` <br> `crlf > crlf` | `lf > lf` <br> `cr > cr` <br> `crlf > crlf` | `lf > lf` <br> `cr > cr` <br> `crlf > crlf` |

#### set in GUI
![git line ending setup](../../screenshot/git-eol.png)
- checkout Windows-style, commit Unix-style line endings:
```bash
$ git config --global core.autocrlf true
```
- Checkout as-is, commit Unix-Style line endings:
```bash
$ git config --global core.autocrlf input
```
- Checkout as-is, commit as-is:
```bash
$ git config --global core.autocrlf false
```

### [please notice](https://git-scm.com/docs/gitattributes#gitattributes-Settostringvalueauto)
> eol
> This attribute sets a specific line-ending style to be used in the working directory. It enables end-of-line conversion without any content checks, effectively setting the text attribute. Note that setting this attribute on paths which are in the index with CRLF line endings may make the paths to be considered dirty. Adding the path to the index again will normalize the line endings in the index.
