<template>
<div class="icons">
    <swiper>
     <swiper-slide v-for="(page,index) of pages" :key="index">
      <div 
         class="icon"
         v-for="item of page"
         :key="item.id"
       >
        <div class="icon-img">
           <img  class="icom-img-content" :src='item.imgUrl'  alt="">
        </div>  
        <p class="icon-desa">{{item.imgText}}</p>
      </div>
     </swiper-slide>
   </swiper>
</div>
</template>

<script>
export default{
    name:'HomeIcons',
    data(){
        return{
            imgList:[{
                id:'001',
                imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png",
                imgText:"热门景点"
          },{
                id:'002',
                imgUrl:"http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png",
                imgText:"热门景点"
          },{
                id:'003',
                imgUrl:"http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png",
                imgText:"热门景点"
          },{
                id:'004',
                imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/50/26ffa31b56646402.png",
                imgText:"海洋馆"
          },{
                id:'005',
                imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png",
                imgText:"动植物园"
          },{
                id:'006',
                imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/bd/9f7b9b2b60c1502.png",
                imgText:"踏青赏花"
          },{
                id:'007',
                imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/a6/6d97515091789602.png",
                imgText:"世界之窗"
          },{
                id:'008',
                imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/e7/d108f17143b40f02.png",
                imgText:"三月特惠"
          },{
                id:'009',
                imgUrl:"http://img1.qunarzz.com/piao/fusion/1803/b6/37560ece9c62b502.png",
                imgText:"东部华侨城"
          }]
        }
    },
    computed:{
        pages(){
            const pages =[]
            this.imgList.forEach((item,index)=>{
                const page = Math.floor(index/8)
                if(!pages[page]){
                    pages[page]=[]
                }
                pages[page].push(item)
            })
            return pages
        }
    }
}

</script>


<style lang="stylus" scoped>
 @import '~@/assets/styles/varibles.styl';
 @import '~@/assets/styles/mixins.styl';
  .icons >>> .swiper-container
    height 0
    padding-bottom:50%
  .icon
    position relative
    overflow hidden
    float:left
    width:25%
    padding-bottom:25%  
    .icon-img
      position absolute
      left:0
      top:0
      right:0
      bottom:.44rem
      .icom-img-content
        height:100%
        display:block
        margin:0 auto
    .icon-desa
      position absolute
      left:0
      right:0
      bottom:0
      height:0.44rem
      line-height:0.44rem
      text-align:center
      color:$dackTextColor
      ellipsis()
</style>