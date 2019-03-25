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
           <img  class="icom-img-content" src='../../../assets/styles/iconfont/tubiao.png'  alt="">
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
                imgUrl:"../../../assets/styles/iconfont/tubiao.png",
                imgText:"热门景点"
          },{
                id:'002',
                imgUrl:"../../../assets/styles/iconfont/tubiao.png",
                imgText:"热门景点"
          },{
                id:'003',
                imgUrl:"../../../assets/styles/iconfont/tubiao.png",
                imgText:"热门景点"
          },{
                id:'004',
                imgUrl:"../../../assets/styles/iconfont/tubiao.png",
                imgText:"热门景点"
          },{
                id:'005',
                imgUrl:"../../../assets/styles/iconfont/tubiao.png",
                imgText:"热门景点"
          },{
                id:'006',
                imgUrl:"../../../assets/styles/iconfont/tubiao.png",
                imgText:"热门景点"
          },{
                id:'007',
                imgUrl:"../../../assets/styles/iconfont/tubiao.png",
                imgText:"热门景点"
          },{
                id:'008',
                imgUrl:"../../../assets/styles/iconfont/tubiao.png",
                imgText:"热门景点"
          },{
                id:'009',
                imgUrl:"../../../assets/styles/iconfont/tubiao.png",
                imgText:"热门景点"
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