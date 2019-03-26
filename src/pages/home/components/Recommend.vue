<template>
    <div>
        <div class="recommend-title">热门推荐</div>
         <ul>
             <li class="item" v-for="(item,index) in list" :key="index">
                     <img :src='item.imgUrl' alt="" class="item-img">
                 <div class="item-info">
                     <p class="item-title">{{item.title}}</p>
                     <p class="item-desc">{{item.desc}}</p>
                     <button class="item-buttom">查看详情</button>
                 </div>
             </li>
         </ul>
    </div>
</template>
<script>
export default{
    name:"HomeRecommend",
    props:{
        list:Array
    },
    data(){
        return{
            recommendList:[{
                id:"0001",
                imgUrl:"http://img1.qunarzz.com/sight/p0/1903/93/939f4ea1d9f2f58da3.water.jpg_200x200_f57fdf8f.jpg",
                title:"深圳欢乐谷",
                desc:"广东省深圳市南山区华侨城侨城街1号"
            },{
                id:"0002",
                imgUrl:"http://img1.qunarzz.com/sight/p0/1903/93/939f4ea1d9f2f58da3.water.jpg_200x200_f57fdf8f.jpg",
                title:"深圳欢乐谷",
                desc:"广东省深圳市南山区华侨城侨城街1号"
            },{
                id:"0003",
                imgUrl:"http://img1.qunarzz.com/sight/p0/1903/93/939f4ea1d9f2f58da3.water.jpg_200x200_f57fdf8f.jpg",
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
.item
  overflow:hidden
  display:flex
  height:1.9rem
  .item-img
    width:1.7rem
    height:1.7rem
    padding:.1rem
  .item-info
    flex:1
    padding:.1rem
    min-width:0
    .item-title
      line-height:.54rem
      font-size:.32rem
      ellipsis()
    .item-desc
      line-height:.4rem
      color:#ccc
      ellipsis()
    .item-buttom
      line-height:0.44rem
      background #ff9300
      margin-top: .16rem
      color:#fff
      border-radius:.06rem
      padding:0 0.2rem
</style>