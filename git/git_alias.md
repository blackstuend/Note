# git alias


git指令的簡化，可以省去每一次打指令繁複以及就不用去背這些指令了

* 設定全域
```
$ git config --global alias.st status
$ git st
$ git config --global alias.ll "log --oneline --graph"
$ git config --global alias.llAll "log --oneline --decorate --graph --all"
$ git ll
```

* 只秀出最後一筆log

```
$ git config --global alias.last 'log -1 HEAD'
```

* show 出所有alias
```
$ git config --get-regexp alias
$ git config --list | grep alias //在bash可以使用grep的方法
```