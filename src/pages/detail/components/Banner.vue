<template>
<div>
  <div class="banner" @click="handbannerClick">
    <img class="banner-img" src="//img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_600x330_f922b488.jpg" alt="" srcset="">
    <div class="banner-info">
      <div class='banner-tittle'>故宫(AAAAA景区)</div>
      <div class="banner-number">
        <span class='iconfont banner-icon'>&#xe60f;&nbsp;&nbsp;</span>8</div>
    </div>
  </div>
  <common-gallary @cloae="handCloaeClick" :imgs="imgs" v-show ="showGallary"></common-gallary>
</div>
</template>
<script>
import CommonGallary from 'common/gallary/Gallary'
export default {
  mame:'DetailBanner',
  data(){
    return {
      showGallary:false,
      imgs:['//img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_600x330_f922b488.jpg','//img1.qunarzz.com/sight/p0/1507/c1/f623e9c1a6c1c2534e783e5268ddcf5d.water.jpg_r_800x800_24a9e7f5.jpg']
    }
  },
  methods:{
    handbannerClick(){
    this.showGallary = true
},
handCloaeClick(){
  this.showGallary = false;
}
  },
  components:{
    CommonGallary
  }
}
</script>
<style lang='stylus' scoped>
.banner
  position:relative
  overflow:hidden
  height:0
  padding-bottom:55%
  .banner-img
    width:100%
  .banner-info
    display:flex
    position:absolute
    left:0
    right:0
    bottom:0
    line-height:.6rem
    color:#fff
    background-image:linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,0.8))
    .banner-tittle
      flex:1
      font-size:.32rem
      padding:0 .2rem
    .banner-number
      margin-top:.14rem
      padding:0 .4rem
      height :.32rem
      line-height:.32rem
      border-radius:.2rem
      background:rgba(0,0,0,.8)
      font-size:.24rem
      .banner-icon
        font-size:.24rem
</style>
