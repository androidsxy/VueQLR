<template>
  <div>
   <home-header :city="city"></home-header>
   <home-swiper :list="swiperList"></home-swiper>
   <home-icons :list="iconList"></home-icons>
   <home-recommed :list="recommendList"></home-recommed>
   <home-weekend :list="weekendList"></home-weekend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommed from './components/Recommend'
import HomeWeekend from './components/Weekend'
import {mapState} from 'vuex'
//ajxs请求
import axios from 'axios'
export default {
  name: 'Home',
  components:{
      HomeHeader,
      HomeSwiper,
      HomeIcons,
      HomeRecommed,
      HomeWeekend
  },
  data(){
    return{
      listcity:"",
      swiperList:[],
      iconList:[],
      recommendList:[],
      weekendList:[]
    }
  },
  computed:{
    ...mapState(['city'])
  },
  methods:{
    getHomeInfo(){
      axios.get('/api/index.json?city='+this.city)
      .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc(res){
      res = res.data
      if(res.ret&&res.data){
        console.log(res);
        const data = res.data;
        this.city = data.city;
        this.swiperList = data.swiperList;
        this.iconList = data.iconList;
        this.recommendList = data.recommendList;
        this.weekendList = data.weekendList;
      }
    }
  },
  mounted(){
    this.listcity = this.city;
    this.getHomeInfo();
  },
  activated(){
    if(this.listcity!==this.city){
      this.listcity=this.city;
       this.getHomeInfo();
    }
    console.log('activated');
  }
}
</script>

<style>

</style>
