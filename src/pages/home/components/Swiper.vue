<template>
<div class='wrapper'>
    <swiper :options="swiperOption">
    <swiper-slide v-for="item of swiperList" :key="item.id">
        <img class='swiper-img' :src="item.imUrl"/>
    </swiper-slide>
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
  </div>
</template>
<script>
export default{
    name:'HomeSwiper',
    data(){
        return{
            swiperOption:{
                pagination:".swiper-pagination",
                loop:true
            },
            swiperList:[{
                id:'001',
                imUrl:'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/1e4d6daa2f0d2744f963d0777955e78a.jpg_750x200_8fd8e73a.jpg'
            },{
                id:'002',
                imUrl:'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/6b6fd3d9e40b749ac1d189ce80ebb3cc.jpg_750x200_9616e2e7.jpg'
            }]
        }
    }
}

</script>
<style lang='stylus' scoped>
.wrapper >>> .swiper-pagination-bullet-active
    background :#fff !important
.wrapper
  touch-action: none;
  overflow hidden
  width:100%
  height:0
  padding-bottom:31.25%
  .swiper-img
    width:100%
</style>