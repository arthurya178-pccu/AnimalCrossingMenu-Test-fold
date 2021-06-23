<!--顯示單個商品-->

<template>
  <div>
    <span>
      <h3>{{menuItem.title}}</h3>
    </span>
  </div>
</template>
<script>
//上方可以放入menuItem的鍵做使用
export default {
  name: "MenuItem",
  props: ['menuItem'],
}
</script>

<style scoped>

</style>