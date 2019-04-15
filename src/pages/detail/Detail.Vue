<template>
  <div>
   <detail-bannder
   :bannerlist='bannerlist'
   :imgs='imgs'
    ></detail-bannder>
   <detail-header></detail-header>
   <div class="content"><detail-list :list="list"></detail-list></div>
  </div>
</template>
<script>
import DetailBannder from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
//ajxs请求
import axios from 'axios'
export default {
  mame:'Detail',
  components:{
    DetailBannder,
    DetailHeader,
    DetailList
  },
  data(){
    return{
      list:[],
      bannerlist:{},
      imgs:[],
    }
  },
  methods: {
    getCityInfo(){
      var that = this;
      axios.get('/api/detail.json',{
        params:{
          id:this.$route.params.id
        }
      }).then((res) => {
        res = res.data;
        if(res.data&&res.ret){
          res = res.data;
          that.list = res.categoryList;
          that.bannerlist={
            bannerImg:res.bannerImg,
            sightName:res.sightName
          }
          that.imgs = res.gallaryImgs;
        }
      }).catch((err) => {
        console.log(err)
      });
    }
  },
  // //生命周期钩子
  //  mounted(){
  //     this.getCityInfo();
  //     console.log("???????");
  //   },
    activated(){
       this.getCityInfo();
      console.log("???????");
    }
}
</script>
<style lang='stylus' scoped>
.content
  height:50rem
</style>
