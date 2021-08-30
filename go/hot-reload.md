# GO Hot Reload 的工具

## Description
由於以前寫vue或是express都會搭配一些hot reload的工具,而剛開始練習go時實在覺得不能自動更新,渾身不舒服
,於是找到以下工具來做使用,我只使用他的基本操作,所以用起來滿容易的,更新也很快

### Installation

```
$ curl -sSfL https://raw.githubusercontent.com/cosmtrek/air/master/install.sh | sh -s -- -b $(go env GOPATH)/bin

$ air -v

```

### Usage

.air.toml 是這個air的設定檔,不更改使用起來就已經滿方便的,日後有需要會先做更新

```
$ cd /path/to/your_project
$ air init
$ air -c .air.toml
```

參考:https://github.com/cosmtrek/air
