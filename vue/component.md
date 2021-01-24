# Vue component 幾種常見的使用方法

## 介紹
Vue component可以將每個組件分開拆開或是組裝，在Vue-cli使用上更多，將每個組件都分別拆開或是組裝，在開發上也可以重複使用

## 使用

* 在component中data是個函式，所以在做宣告時一定要用function的方式加上return，特別是在Vue-cli是將所以元素都拆成component

### 全域宣告

```html
<body>
    <button-counter></button-counter>
</body>
<script>
Vue.component('button-counter', {
  data: function () {
    return {
      count: 0
    }
  },
  template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
})
</script>
```



### Local註冊

```javascript
var button_counter = {
  data: function () {
    return {
      count: 0
    }
  },
  template: '<button v-on:click="count++">You clicked me {{ count }} times.</button>'
};

var vm = new Vue({
  el: '#app',
  components: {
    button_counter,
  }
});
```


### 使用x-template

* 這是在看六角學院Vue課程中推薦的，可以將html與script徹底分開，使用上我覺得視覺更為舒服，排版也美觀，各人目前最喜歡用這個，

```html
<script type="text/x-template" id="button_counter">
  <button v-on:click="count++">You clicked me {{ count }} times.</button>
</script>

<script>
    // 全域註冊
    Vue.component('button_counter', {
        template: '#button_counter',
            data: function () {
                return {count: 0}
        },
    })  

    // 區域註冊
    const button_counter = {
        template: '#button_counter',
        data: function () {
            return {count: 0}
    }
    var vm = new Vue({
        el: '#app',
        components: {
            button_counter,
        }
    });
    
</script>
```

## is來實現動態更改template

* 如果有兩個component需要做切換，通常可以用is來實現動態雖然使用v-if也可以~

* 以下範例按下按鈕則會將裡面chose的值改成hello_world，上面的template也會跟著做切換

```html
<body>
    <div :is="chose">
    <button @click="chose='hello_world'">切換組件</button>
</body>
<script>
    var vm = new Vue({
        el: '#app',
        data:{
            chose:"button_counter"
        }
        components: {
            button_counter,
            hello_world,
        }
    });
</script>
```