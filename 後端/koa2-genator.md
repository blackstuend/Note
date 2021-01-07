# 使用koa2 的cli

* Installation

```
$ npm install -g koa-generator
```


* Usage
```
$ koa2 /tmp/foo && cd /tmp/foo
```

* 使用ejs模板


```
$ koa2 /tmp/foo  -e && cd /tmp/foo
```

* 以下為可以用的參數
````
-h, --help          output usage information
-V, --version       output the version number
-e, --ejs           add ejs engine support (defaults to jade)
    --hbs           add handlebars engine support
-n, --nunjucks      add nunjucks engine support
-H, --hogan         add hogan.js engine support
-c, --css <engine>  add stylesheet <engine> support (less|stylus|compass|sass) (defaults to plain css)
    --git           add .gitignore
-f, --force         force on non-empty directory
````

參考:https://www.npmjs.com/package/koa-generator