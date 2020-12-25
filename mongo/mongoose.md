# Mongoose

## Introduction
* mongoose是一個node.js用來管理mongodb的API
* 使用的語法與mongodb相似
* 可以使得database也能夠擁有schema，管理時更方便

## INSTALL

```shell
$ npm install mongoose 
```



## GetStart


```javascript
const mongoose = require("mongoose")
var mongoDB = 'mongodb://127.0.0.1/my_database';
mongoose.connect(mongoDB,{useCreateIndex: true,useUnifiedTopology: true,useNewUrlParser: true,autoIndex:false});
mongoose.set('useNewUrlParser', true); //全域的設定，當如果建立多個connection，可用set，就不用在每個connect上面添加
```
### option解析
* 在最新版{useCreateIndex: true,useUnifiedTopology: true,useNewUrlParser: true}會要求你加入這些參數，雖然不加也能跑，但會有一些[Warning](https://mongoosejs.com/docs/deprecations.html)
    * useNewUrlParser : 主要用來解析URL，default為false，如果不加則需要填入port，像是:mongodb://localhost:27017/dbname，加入後可移除port:mongodb://localhost/dbname
    * createIndex:預設為false，原先是使用createIndex，但在新版本已被棄用，現在都使用createIndex
    * autoIndex:預設為true，建議改為false，然後自行建立index，在搜尋時會較為快速
    * useUnifiedTopology:可針對連線的一些設定，timeout機制之類，需要調為true才不會有warning
## Define Schema

```javascript
  import mongoose from 'mongoose';
  const { Schema } = mongoose;

  const blogSchema = new Schema({
    title:  String, // String is shorthand for {type: String}
    author: String,
    body:   String,
    comments: [{ body: String, date: Date }],
    date: { type: Date, default: Date.now },
    hidden: Boolean,
    meta: {
      votes: Number,
      favs:  Number
    }
  });
```
* schema 新增項目

```javascript
const schema2 = new Schema({
  test: {
    type: String,
    required: true, //必須傳值，否則回傳err
    default:"test", // 沒有value,自動代入
    index: true, //是否建立index
    unique: true //確認是否有一樣的,如果有回傳err
  }
});
```

* Schema常用
    * String
    * Number
    * Date
    * Boolean
    * Array

## Package

* 使用model進行封裝
```javascript
  import mongoose from 'mongoose';
  const { Schema } = mongoose;

  const blogSchema = new Schema({
    title:  String, // String is shorthand for {type: String}
    author: String,
    body:   String,
    Date: Date
  });
  let Blog_db = mongoose.model("blog",blogSchema)
```
* Model 常用函式
    * 使用async await
1. Insert or save
    
```javascript
let data = {title:"test",author:"blackfloat",body:"this is test",Date:new Date()}
await new Blog_db(data).save()
```

2. Find
    * 第2個參數為option，可只找出那些欄位
```javascript
await Blog_db.findOne({title:"test"})
await Blog_db.findOne({title:"test"},{title:1})
```

3. update更新
    * 
```javascript
await Blog_db.updateOne({title:'test'},{title:"hello"})
```

4. remove

```javascript
await Blog_db.deleteOne({title:'test'},{title:"hello"})
```

參考資料:https://mongoosejs.com/