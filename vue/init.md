# Vue-Cli 安裝


## Installation 
```
$ npm install vue-cli -g
```

## Usage
* vue init 預設是使用vue 2的版本
```
$ vue init <template> <project-name>
```
查看有哪些template 可使用
```
$ vue list
```



* Vue create 可選擇vue2 or vue3

```
$ vue create 
```


```
$ cd project-name 
$ npm i
```

* 啟動
```
$ npm run dev
```


* 安裝其他工具
1. sass
2. vue-router
3. axios

修改package.json
```
  "dependencies": {
    "axios": "^0.21.1",
    "bootstrap": "^4.5.3",
    "node-sass": "^4.14.1",
    "sass-loader": "^7.0.3",
    "vue": "^2.5.2",
    "vue-axios": "^3.2.1",
    "vue-router": "^3.4.9",
    "popper.js": "^1.16.1",
    "jquery": "^3.5.1",
  }
```

也可直接安裝

* 需住要安裝sass如果安裝新版在vue-cli中使用可能會報錯，所以建議用舊版
```
$ npm install axios vue-axios vue-router sass-loader@7.0.3 node-sass@4.14.1 jquery popper --save
```

