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
      city:"",
      swiperList:[],
      iconList:[],
      recommendList:[],
      weekendList:[]
    }
  },
  methods:{
    getHomeInfo(){
      axios.get('/api/index.json')
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
    this.getHomeInfo();
  }
}
</script>

<style>

</style>
