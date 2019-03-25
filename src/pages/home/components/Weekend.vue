<template>
    <div>
        <div class="recommend-title">周末去哪</div>
         <ul>
             <li class="item" v-for="(item,index) in recommendList" :key="index">
                <div class="item-img-wrapper">
                   <img :src='item.imgUrl' alt="" class="item-img">
                </div>
                 <div class="item-info">
                     <p class="item-title">{{item.title}}</p>
                     <p class="item-desc">{{item.desc}}</p>
                 </div>
             </li>
         </ul>
    </div>
</template>
<script>
export default{
    name:"HomeWeekend",
    data(){
        return{
            recommendList:[{
                id:"0001",
                imgUrl:"http://img1.qunarzz.com/sight/source/1811/15/66f14e0fd6fbb.jpg_r_640x214_5d69f21d.jpg",
                title:"深圳欢乐谷",
                desc:"广东省深圳市南山区华侨城侨城街1号"
            },{
                id:"0002",
                imgUrl:"http://img1.qunarzz.com/sight/source/1811/15/66f14e0fd6fbb.jpg_r_640x214_5d69f21d.jpg",
                title:"深圳欢乐谷",
                desc:"广东省深圳市南山区华侨城侨城街1号"
            },{
                id:"0003",
                imgUrl:"http://img1.qunarzz.com/sight/source/1811/15/66f14e0fd6fbb.jpg_r_640x214_5d69f21d.jpg",
                title:"深圳欢乐谷",
                desc:"广东省深圳市南山区华侨城侨城街1号"
            }]
        }
    }
}
</script>
<style lang="stylus" scoped>
 @import '~@/assets/styles/mixins.styl';
.recommend-title
  margin-top:.2rem
  line-height:.8rem
  text-indent:.2rem
  background:#9999
.item-img-wrapper
  overflow hidden
  height:0
  padding-bottom:33.9%
  .item-img
    width:100%
.item-info
    padding:.1rem
    .item-title
      line-height:.54rem
      font-size:.32rem
      ellipsis()
    .item-desc
      line-height:.4rem
      color:#ccc
      ellipsis()
</style>