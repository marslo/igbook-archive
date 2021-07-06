# hexo

**Table of Contents** _generated with_ [_DocToc_](https://github.com/thlorenz/doctoc)

* [prepare](hexo.md#prepare)
* [init](hexo.md#init)
* [add theme](hexo.md#add-theme)
  * [clone code](hexo.md#clone-code)
  * [install plugin](hexo.md#install-plugin)
  * [generate new pages](hexo.md#generate-new-pages)
  * [diable the default highlight settings](hexo.md#diable-the-default-highlight-settings)

## prepare

```bash
$ npm i -g hexo-cli
```

## init

```bash
$ mkdir myblog && cd myblog
$ hexo init
```

```bash
  $ hexo init
  INFO  Cloning hexo-starter https://github.com/hexojs/hexo-starter.git
  INFO  Install dependencies
  added 183 packages from 421 contributors and audited 189 packages in 22.277s

  12 packages are looking for funding
    run `npm fund` for details

  found 0 vulnerabilities

  INFO  Start blogging with Hexo!
```

## add theme

> credit belongs to [snark](https://github.com/Litreily/hexo-theme-snark)

### clone code

$ git submodule add [https://github.com/imarslo/hexo-theme-snark.git](https://github.com/imarslo/hexo-theme-snark.git) themes/snark

$ git clone [https://github.com/imarslo/hexo-theme-snark.git](https://github.com/imarslo/hexo-theme-snark.git) themes/snark $ sed '/highlight:/{n;s/^._$/  enable: false/}' -i \_config.xml $ sed '/highlight:/{n;n;s/^._$/  line\_number: false/}' -i \_config.xml

$ git submodule sync --recursive $ git submodule update --init --recursive

### install plugin

```bash
$ npm install hexo-renderer-pug --save
$ npm install hexo-renderer-sass --save
$ npm install hexo-generator-feed --save
$ npm install hexo-generator-search --save
$ npm install hexo-generator-sitemap --save
```

### generate new pages

```bash
$ hexo new page archives
$ hexo new page categories
$ hexo new page tags
$ hexo new page about
```

### diable the default highlight settings

> default settings in `_config.xml`

$ sed '/highlight:/{n;s/^._$/  enable: false/;n;s/^._$/  line\_number: false/;}' -i \_config.xml

$ sed '/highlight:/{n;s/^._$/  enable: false/}' -i \_config.xml $ sed '/highlight:/{n;n;s/^._$/  line\_number: false/}' -i \_config.xml

$ grep highlight: \_config.yml -A 6 highlight: enable: false line\_number: false auto\_detect: false tab\_replace: '' wrap: true hljs: false

