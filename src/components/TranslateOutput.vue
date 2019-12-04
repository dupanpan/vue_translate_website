<template>
  <div id="translateOutput">
      <h2>{{translatedText}}</h2>
      <!-- <h2>vfdgfdgfg</h2> -->

  </div>
</template>

<script>
// 父组件给子组件传值使用props
export default {
    name:'translateOutput',
    props:["translatedText"],
}
</script>

<style scoped>
 
</style>
