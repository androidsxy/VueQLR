<template>
    <ul class="list">
        <li class="item" 
        v-for="item of letters" 
        :key="item"
        @touchstart="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchEnd"
        @click="handleLetterClick"
        :ref="item"
        >{{item}}
        </li>
    </ul>
</template>
<script>
export default{
    name:"CityAlphabet",
    props:{
        cities:Object
    },
    //计算属性
    computed:{
        letters(){
            const letters = [];
            for(let i in this.cities){
                letters.push(i);
            }
            return letters
        }
    },
    data(){
        return{
            touchStatus:false,
            startY:0
        }
    },
    updated(){
        this.startY = this.$refs['A'][0].offsetTop;
    },
    methods:{
        handleLetterClick(e){
            //触发组件事件
            this.$emit('change',e.target.innerText)
        },
        handleTouchStart(){
            this.touchStatus = true; 
        },
        handleTouchMove(e){
            if(this.touchStatus){
                if(this.timer){
                    clearTimeout(this.timer)
                }
                //提高网站性能
                this.timer = setTimeout(()=>{
                   const touchY = e.touches[0].clientY-79
                   const index = Math.floor((touchY-this.startY)/20)
                   if(index>=0&&index<this.letters.length){
                       this.$emit('change',this.letters[index]);
                }
                },16)
            }
        },
        handleTouchEnd(){
            this.touchStatus =false;
        }
    }
}
</script>
<style lang='stylus' scoped>
@import '~@/assets/styles/varibles.styl'
.list
/*垂直居中*/
  display:flex
  flex-direction:column
  justify-content:center
  position:fixed
  right:0
  top:1.58rem
  bottom:0
  width:.4rem
  .item
    line-height:.4rem
    text-align:center
    color:$bgColor
</style>