<template>
 <div class="list" ref="wrapper">
   <div>
    <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="buttom-list">
            <div class="buttom-wrapper">
               <div class="buttom">{{this.currdcity}}</div>
            </div>
        </div>
     </div>
   <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="buttom-list">
            <div class="buttom-wrapper"
            v-for='item of hotCities'
            :key="item.id"
            @click="handleCityClick(item.name)"
            >
               <div class="buttom">{{item.name}}</div>
            </div>
        </div>
     </div>
    <div class="area"
     v-for='(item,key) of cities'
     :key="key"
     :ref="key"

     >
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list">
            <div class="item border-bottom"
            v-for='innrItem of item'
            :key="innrItem.id"
             @click="handleCityClick(innrItem.name)"
            >{{innrItem.name}}</div>
        </div>
    </div>
   </div>
 </div>
</template>
<script>
import Bscroll from 'better-scroll'
import {mapState,mapMutations} from 'vuex'
export default{
    name:"CityList",
    props:{
        hotCities:Array,
        cities:Object,
        letter:String
    },
    computed: {
      ...mapState({
        currdcity:'city'
      })
    },
    methods:{
        handleCityClick(city){
            this.changeCity(city)
            this.$router.push('/')
        },
        ...mapMutations(['changeCity'])
    },
    mounted(){
        this.scroll = new Bscroll(this.$refs.wrapper, { mouseWheel: true, click: true, tap: true });
    },
    //vue自带监听 当letter改变时
    watch:{
        letter(){
            if(this.letter){
                const element = this.$refs[this.letter][0]
                this.scroll.scrollToElement(element);
            }
        }
    }
}
</script>
<style lang='stylus' scoped>
@import '~@/assets/styles/varibles.styl'
.border-topbottom
  &:before
    border-color:#ccc
  &:after
    border-color:#ccc
.border-bottom
  &:before
    border-color:#ccc
.list
 overflow:hidden
 position:absolute
 top:1.58rem
 left:0
 right:0
 bottom:0
 .title
  line-height:.54rem
  background:#eee
  padding-left:.2rem
  color:#666
  font-size :.26rem
.buttom-list
  padding:.1rem .6rem .1rem .1rem
  overflow hidden
  .buttom-wrapper
    float:left
    width:33.33%
    .buttom
      margin:.1rem
      text-align:center
      border:.02rem solid #ccc
      padding:.1rem 0
      border-radius:.06rem
.item-list
  .item
    line-height:.76rem
    color:#666
    padding-left:.2rem
</style>
