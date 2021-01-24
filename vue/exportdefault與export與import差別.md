# export 與 import 解析

## 介紹

export 與 import 是javascript ES6新的引用方式，類似於python的感覺，
有些瀏覽器或是node.js舊版尚未支援來替代module.exports，使用上更為簡便

## 瀏覽器中
在瀏覽器中如果需要用到export 與 import 需要再script上面加上type="module"
```html
<script type="module"></script>
```

但有些瀏覽器可能不支援可使用以下
```html
<!-- 支援 module 語法的新瀏覽器 -->
<script type="module" src="module.js"></script>

<!-- 不支援 module 語法此段會被新型瀏覽器忽略 -->
<script nomodule src="IENotGood.js"></script>
```


## 最常見export default

* 在使用vue-cli時常常這樣寫來輸出component

count.vue
```javascript
export default {
    data(){
        return {
            data:1,
        }
    }
}
```

* 使用

main.js
```javascript
import Count from "./count.vue";
```

## export
 

count.vue
```
export const Count = {
    data(){
        return {
            data:1,
        }
    }
}
export const people = {
    data(){
        return {
            data:1,
        }
    }
}
```

* 使用

main.js
```javascript
import {Count,people} from "./count.vue";
import * as name from "./count.vue";
console.log(name.Count.data());
```


## 感想

* 最大的差別就是只單純用export是需要一個一個解構的或是使用"*" 來匯出全部東西，其實感覺就跟python真的是很像，學習上真的很方便~


參考:https://wcc723.github.io/development/2020/03/25/import-export/