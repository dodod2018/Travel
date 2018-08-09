<template>
  <div class="container">
    <router-link to="/">
      <div class="transparent">
        <span class="iconfont icon-fanhui"></span>
      </div>
    </router-link>
    <div v-show="showHeader" class="truth" :style="opacityStyle">
      <router-link to="/">
        <span class="iconfont icon-fanhui"></span>
      </router-link>
      <span class="header-text">城市选择</span>
    </div>
  </div>
</template>
<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showHeader: false,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const scrollTop = document.documentElement.scrollTop
      let opacity
      if (scrollTop > 70) {
        opacity = scrollTop / 160
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {
          opacity
        }
        this.showHeader = true
      } else {
        this.showHeader = false
      }
      console.log(scrollTop)
    }
  },
  activated () {
    window.addEventListener('scroll', this.handleScroll)
  },
  deactivated () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
  .container
    position absolute
    height 50rem
    top 0
    left 0
    width 100%
    .transparent
      position absolute
      top .2rem
      left .2rem
      width .6rem
      height .6rem
      line-height .6rem
      text-align center
      border-radius 50%
      background-color rgba(0,0,0,.8)
      .iconfont
        color #fff
        position relative
        left -.02rem
    .truth
      position fixed
      top 0
      height .86rem
      background-color $bgColor
      display flex
      z-index 1
      width 100%
      color white
      align-items center
      color #fff
      .iconfont
        font-size .4rem
        color #fff
      .header-text
        flex 1
        text-align center
</style>
