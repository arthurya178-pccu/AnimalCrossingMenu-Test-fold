<template>
  <div id="app">
    <MyMenu/> <!--呼叫MyMenu 樣板-->

  </div>
</template>

<script>
import MyMenu from './components/menu.vue'

export default {
  name: 'App',
  components: {
    MyMenu //使用下層MyMenu
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body
{
  background: #caffeb;
}
</style>
