# Nuxt 使用notification-vue

## Install

* 安裝
```
$ npm install --save vue-notification
```

* 將元件加到plugin
1. 需要加client 和 ssr版本才不會有報錯

* 雖然使用Vue.use(Notifications)就可以使用Vue.$notify了，但如果要在store裡面使用需要做inject

./plugin/notifications-client.js
```js
import Notifications from 'vue-notification'
import Vue from 'vue'

Vue.use(Notifications)

export default (context, inject) => {
  inject('notify', Vue.notify)
}

```

./plugin/notifications-ssr.js
```js
import Vue from 'vue'
import Notifications from 'vue-notification/dist/ssr.js'

Vue.use(Notifications)
```

## Usage

```html
<template>
  <div>
    <notifications group="all" />
    <notifications group="test" />
    <button @click="show">click</button>
    <button @click="show2">click2</button>
  </div>
</template>

<script>
export default {
  methods: {
    show() {
      this.$notify({ group: 'all', text: 'Heyy !!!', type: 'warn' })
    },
    show2() {
      this.$notify({ group: 'test', text: 'test !!!', type: 'success' })
    }
  },
}
</script>
```

* 如果是在store內使用

```js
export const actions = {
  add(state, text) {
    this.$notify({
      group: 'all',
      title: 'test!',
      text: 'test text',
      type: 'success',
    })
  },
}

```