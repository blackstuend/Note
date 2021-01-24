# Github API

## 介紹
可以取得Github的user 資料或是repository等等



## 使用

* 取得所有repository

使用axios
```javascript
let api = "https://api.github.com/users/blackstuend/repos";
axios.get(api).then((res)=>{
    console.log(res.data);
})
```

* 分頁取得repository

* page=1 為第1頁,per_page為一次取得幾筆資料，即這邊為第1頁取5筆資料~
* 有嘗試過因為我的repository只有17筆，但是page改成5會取得一個空陣列，並不會自動循環

```javascript
let api = "https://api.github.com/users/blackstuend/repos?page=1&per_page=5";
axios.get(api).then((res)=>{
    console.log(res.data);
})
```


- Github實作:https://github.com/blackstuend/blackfloat.github.io
- Demo:https://blackstuend.github.io/blackfloat.github.io/


參考資料:'https://api.github.com/user/repos?page=2&per_page=100'