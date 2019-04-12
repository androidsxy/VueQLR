<template>
  <div>
   <detail-bannder></detail-bannder>
   <detail-header></detail-header>
   <div class="content"></div>
  </div>
</template>
<script>
import DetailBannder from './components/Banner'
import DetailHeader from './components/Header'
export default {
  mame:'Detail',
  components:{
    DetailBannder,
    DetailHeader
  }
}
</script>
<style lang='stylus' scoped>
.content
  height:50rem
</style>
