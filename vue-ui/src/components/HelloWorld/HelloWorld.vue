<template>
  <div class="hello">
    <div class="top">{{title}}</div>
    <div v-for="item in items">
      <div>
        <img src="item.src" alt="">
        <!-- <p>{{value}}</p> -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      title:'Direct From Manufacturer',
      items:[
        {"src":'./images/vue1.jpg'}
      ]
    }
  }
}
</script>

<style lang="less" src="./HelloWorld.less"></style>
