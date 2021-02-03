# git remote 

* 顯示遠端的資料位置，搭配github，需先git clone

```
$ git remote -v 
```

* 新增遠端資料庫

```
$ git remote add upstream https://github.com/blackstuend/Note.git
```


* 查看完整遠端訊息

```
$ git remote show origin
```

* 更改git remote 名稱

```
$ git remote rename upstream new_upstream
```