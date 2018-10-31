<template>
    <div class="app">
        
        <div class="top">
            <div :class="isfixed == true ? 'fix' :''" id="title" v-show="isActive">
                <img :src=left alt="" class="one">
                {{title}}
            </div>
            <img :src="topPic" alt="" class="two">
        </div>
        <div class="words_con">
            <h3 class="top_tit">{{topTit}}</h3>
            <p class="top_con">{{topCon}}</p>
        </div>
        <div  class="all">
            <div class="list" v-for="i in list">
                <img :src="i.mainPic" alt="">
                <div class="list_con">
                    <p class="production odd-ellipsis">{{i.name}}</p>
                    <p class="price">${{i.price}}</p>
                </div>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    data () {
        return {
            list:[
            ],
            isfixed:false,
            topPic:'',
            topTit:'',
            topCon:'',
            title:'dhdhdhdhdhdhdhdhdhdh',
            left:'././images/left.png',
            isActive:true,
        }
    },
    created () {
        let vm=this;
        console.log(vm.$route.query.bsid)
        let id=vm.$route.query.bsid;
        vm.axios.get('https://www.easy-mock.com/mock/5bd00f2fdfa1f337facb9f59/chong/factory-product/'+id)
        .then(function(response){
                console.log(response)
                vm.list=response.data.data.list;
                vm.topPic=response.data.data.factoryinfo.picDetail;
                vm.topTit=response.data.data.factoryinfo.name;
                vm.topCon=response.data.data.factoryinfo.subtitle;
            })
        .catch(function(){

        })
    },
    methods: {
        
    },
    mounted () {
        // // 监听滚动事件
        let vm=this;
        window.addEventListener("scroll",function(){
            let scrollTop = window.pageYOffset || document.documentElement.scrollTop || document.body.scrollTop;
            console.log("p")
            if (scrollTop > 200) {
                console.log("dasffsdfsdfs")
                vm.isfixed = true;
                vm.isActive=true;
                } else {
                vm.isfixed = false
                vm.isActive=false;
            }
        })
    }
    
}
</script>
<style scoped lang="less" src="./second.less"></style>

