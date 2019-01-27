<template>
  <div class="hello">
    <md-button @click="zml">底部弹出</md-button>
    <my-dailog :myShow="isPopupShow"></my-dailog>
  </div>
</template>

<script>
import { Button } from 'mand-mobile'
import MyDailog from './dailog'

export default {
  name: 'HelloWorld',
  data () {
    return {
      isPopupShow: false
    }
  },
  components: {
    [Button.name]: Button,
    MyDailog
  },
  methods: {
    zml () {
      this.isPopupShow = !this.isPopupShow
      console.log('hello world', this.isPopupShow)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='stylus' scoped>
h1, h2 {
  font-weight: normal;
}
.md-button.primary {
  width 300px
}
</style>
