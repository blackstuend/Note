# git merge


* 直接使用git merge

```bash
$ git llAll
* 3fc5dce (HEAD -> master) push
* cef8f59 master commit
| * 83b498f (testing) testing update
|/
* 85c144b second commit
* 5ddb50a "first time commit"

$ git merge testing
$ git llAll
*   486754b (HEAD -> master) Merge branch 'testing'
|\
| * 83b498f (testing) testing update
* | 3fc5dce push
* | cef8f59 master commit
|/
* 85c144b second commit
* 5ddb50a "first time commit"
```

* 加上-m 參數
    - 則可以寫下commit的content
```
$ git merge testing -m "merge branch"
```

