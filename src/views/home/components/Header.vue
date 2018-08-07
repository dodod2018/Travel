<template>
    <div class="header">
      <div class="header-left">
        <span class="iconfont icon-fanhui"></span>
      </div>
      <div class="header-center">
        <span class="iconfont icon-sousuo"></span>
        输入城市/景点/游玩主题
      </div>
      <div class="header-right">
        城市
        <span class="iconfont icon-jiantouarrow486"></span>
      </div>
    </div>
</template>
<script>
export default {
  name: 'HomeHeader'
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'

.header
  display: flex;
  justify-content: space-between
  background-color: $bgColor
  align-items: center
  height: 0.86rem
  color: #fff
  .iconfont
    font-size: .4rem
  .header-left
    width: .64rem
    text-align: center
  .header-center
    height: 0.64rem
    line-height: 0.64rem
    background-color: white
    border-radius: .1rem
    color: #ccc
    flex: 1
    padding-left: .2rem
    *
      vertical-align: middle
    span
      font-size: .3rem
  .header-right
    width:1.4rem
    text-align: center
    span
      vertical-align: middle
</style>
