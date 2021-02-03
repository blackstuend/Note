# git reset and checkout
* 在git的回到過去，試著讓故事繼續

## reset --hard 用法
* 將資料與狀態全部回復
* 所以使用完再去git status是空的
* 最為常用

回復到HEAD
```
$ git reset --hard HEAD
```

回復到HEAD的上一個
```
$ git reset --hard HEAD^
$ git reset --hard HEAD~1
```

回復到前面好幾個
```
$ git reset --hard HEAD~5
```

使用SHA-1的名稱
* 使用前面4碼即可
```
$ git reset bfc4 --hard
```

* 回到前面版本，顯示出後面版本
    - reflog = reference log 這是處理資料完整的資訊，可以藉由這個參數看到之前的動作及SHA-1名稱
```
$ git reflog
```

## git reset --mixed
* mixed為預設的option
* 與hard差別在於,他沒將資料夾回覆，他只有將commit以及stage回覆

```
$ git llAll
* 677c4d4 (HEAD -> master) checkout2
* 150d9f8 checkout
*   bfc4b52 Merge branch 'testing'
|\
| * db55a91 (testing) testing2
| * 83b498f testing update
* | cef8f59 master commit
|/
* 85c144b second commit
* 5ddb50a "first time commit"
$ git reset 150d
Unstaged changes after reset:
M       cool.txt
$ git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   cool.txt

no changes added to commit (use "git add" and/or "git commit -a")
```
* 由上述可知回到未被add之前，也就是stage之前
* 要先add在commit在能完成新的commit


## git reset --soft
* 回到commit 之前，add之後

```
$ git ll
* 677c4d4 (HEAD -> master) checkout2
* 150d9f8 checkout
*   bfc4b52 Merge branch 'testing'
|\
| * db55a91 (testing) testing2
| * 83b498f testing update
* | cef8f59 master commit
|/
* 85c144b second commit
* 5ddb50a "first time commit"
$ git reset 150d --soft
$ git status
On branch master
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   cool.txt
```
* 直接commit 即可生成新的資料


## 使用checkout 的方法

* 大部分跟reset都很像，差別在於reset回到之前版本時在使用git log會看不到紀錄，而checkout則可以看到
```
$ git llAll
* 677c4d4 (HEAD -> master) checkout2
* 150d9f8 checkout
*   bfc4b52 Merge branch 'testing'
|\
| * db55a91 (testing) testing2
| * 83b498f testing update
* | cef8f59 master commit
|/
* 85c144b second commit
* 5ddb50a "first time commit"
```

開始使用可以看到HEAD的位置變了，但是由於上面是還有commit時再做commit由於會有衝突所以是在做紀錄時建議轉到新增另一個branch來做使用
```
$ git checkout 150d
$ git llAll
* 677c4d4 (master) checkout2
* 150d9f8 (HEAD) checkout
*   bfc4b52 Merge branch 'testing'
|\
| * db55a91 (testing) testing2
| * 83b498f testing update
* | cef8f59 master commit
|/
* 85c144b second commit
* 5ddb50a "first time commit"
```

* 回復單個資料
```
$ git checkout HEAD^ -- cool.txt
```

