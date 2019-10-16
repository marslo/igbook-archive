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
