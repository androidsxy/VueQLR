<template>
    <ul class="list">
        <li class="item">a</li>
        <li class="item">a</li>
        <li class="item">a</li>
    </ul>
</template>
<script>
export default{
    name:"CityAlphabet"
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