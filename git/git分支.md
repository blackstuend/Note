# Git branch

* 新增分支

```
$ git branch testing
```

* 轉換分支
    - 他會繼承master之前的所有資料
```
$ git checkout testing
```

* 查看log


```
$ git log --oneline --graph
```

* 查看所有分支log


```
$ git log --oneline --decorate --graph --all
$ git config --global alias.llAll "log --oneline --decorate --graph --all" //寫入alias
```

* 新增branch並轉換過去

```
$ git checkout -b testing2
```

