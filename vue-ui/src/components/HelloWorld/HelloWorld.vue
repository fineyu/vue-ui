<template>
  <div class="hello">
    <div class="top">{{title}}</div>
    <div v-for="(i, index) in list" @click="jump(index)" >
        <div class="list" >
          <img :src="i.picDetail" alt="">
          <p>{{i.name}}</p>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      index:'',
      title:'Direct From Manufacturer',
      list:[
       
      ],
    
    }
  },
  methods:{
    jump:function(index){
        var uid=this.list[index].bsid;
        this.$router.push({path:'/second',query:{bsid:uid}});
    }
  },
  created () {
      let vm=this;
      vm.axios.get('https://www.easy-mock.com/mock/5bd00f2fdfa1f337facb9f59/chong/factory')
        .then(function (response) {
        vm.list=response.data.data.list
        // console.log(response.data.data.list[0].bsid)
        
      })
      .catch(function (error) {
        console.log(error);
      });
  }
}
</script>

<style scoped lang="less" src="./HelloWorld.less"></style>


