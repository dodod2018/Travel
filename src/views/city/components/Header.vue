<template>
  <div class="header">
    城市选择
    <router-link to="/">
      <span class="iconfont icon-fanhui"></span>
    </router-link>
  </div>
</template>
<script>
export default {
  name: 'cityHeader'
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
  .header
    position relative
    height $headerHeight
    line-height $headerHeight
    background-color $bgColor
    text-align center
    color #fff
    .icon-fanhui
      position absolute
      font-size .4rem
      left 0
      top 0
      padding-right .2rem
      padding-left .1rem
      color #fff
</style>
