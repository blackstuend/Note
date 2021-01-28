# 使用Css做出zoom的效果

## 介紹

* 使用transform中的scale屬性即可縮放
* 必須先分別限制外層與內層，由於如果直接進行scale縮放是整個元素都會變，內層放要縮放資料，外層寬高則跟內層相同，加入overflow:hidden，即可做出縮放


```html
<div class="zoom_parent">
  <div class="zoom"></div>  
</div>
<style>
    .zoom_parent{
    overflow:hidden;
    width: 200px;
    height: 200px;
    }
    .zoom{
    background-image:url(https://images.unsplash.com/photo-1611826647488-0a13e6a358b3?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=562&q=80);
    height: 200px;
    width:200px;
    background-size: cover;
    background-position: center center ;
    transform: scale(1.0);
    transition: all 1s ;
    }

    .zoom:hover{
    transform: scale(1.2);
    }
</style>
```


* codepen:https://codepen.io/sheng-wei-lin/pen/ExNYqZm