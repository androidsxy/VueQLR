<template>
<div>
    <div class="search">
        <input v-model="keyword" type="text" placeholder="输入城市名或拼音" class="search-input">
    </div>
    <div
        class="search-city"
        ref="seach"
        v-show="keyword">
        <ul>
            <li class="seach-item border-bottom"
            v-for="item in list"
            :key="item.id"
            @click="handleCityClick(item.name)"
            >{{item.name}}</li>
            <li v-show="hasNoData" class="seach-item border-bottom">没有找到数据</li>
        </ul>
    </div>
</div>
</template>
<script>
import Bscroll from 'better-scroll'
import {mapMutations} from 'vuex'
export default{
    name:"CitySeach",
    props:{
        cities:Object
    },
    data(){
        return{
            keyword:"",
            list:[],
            timer:null
        }
    },
    methods:{
          handleCityClick(city){
            this.changeCity(city)
            this.$router.push('/')
        },
        ...mapMutations(['changeCity'])
    },
    watch:{
        keyword(){
            if(this.timer){
                clearTimeout(this.timer)
            }
            if(!this.keyword){
                this.list=[];
                return
            }
            this.timer = setTimeout(()=>{
                const result =[];
                for (let i in this.cities){
                    this.cities[i].forEach(element => {
                        if(element.name.indexOf(this.keyword)>=0){
                            result.push(element);
                        }
                        if(element.spell.indexOf(this.keyword)>=0){
                            result.push(element);
                        }
                    });
                }
                this.list = result;
            },100);
        }
    },
    mounted(){
        this.scroll = new Bscroll(this.$refs.seach)
    },
    //计算
    computed:{
        hasNoData(){
            return !this.list.length
        }
    }
}
</script>
<style lang='stylus' scoped>
@import '~@/assets/styles/varibles.styl'
.search
  height:0.72rem
  padding:0 .1rem
  background:$bgColor
  .search-input
    box-sizing:border-box
    width:100%
    height:.62rem
    padding:0 .1rem
    line-height:.62rem
    text-align:center
    border-radius:.06rem
    color:#666
.search-city
  position:absolute;
  top:1.58rem
  left:0
  right:0
  bottom:0
  overflow:hidden
  z-index:1
  background:#eee
  .seach-item
    line-height :.62rem
    padding left 0.2rem
    background:#fff
    color:#666
</style>
