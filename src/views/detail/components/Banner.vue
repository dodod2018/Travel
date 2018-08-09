<template>
  <div class="banner" @click="handleBannerClick">
    <img src="https://pic4.40017.cn/scenery/destination/2017/03/21/17/6AZx19_640x380_00.jpg" alt="">
    <div class="banner-info">
      <div class="desc">大连圣亚海洋世界（AAAA景区）</div>
      <div class="quantity">
        <span class="iconfont icon-sousuo"></span>
        49
      </div>
    </div>
    <gallary :imgs="imgs" v-show="showGallary" @close="handleBannerClick"/>
  </div>
</template>
<script>
import Gallary from 'components/gallary/Gallary'
export default {
  name: 'DetailBanner',
  components: {Gallary},
  data () {
    return {
      imgs: [
        'https://pic5.40017.cn/02/001/78/36/rBANDFmHwNqAQTx5AAD-3tQiKuk263_640x_02.jpg.webp',
        'https://pic4.40017.cn/gny/line/2016/07/01/09/ibKFHG_640x_02.jpg.webp'
      ],
      showGallary: false
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = !this.showGallary
    }
  }
}
</script>
<style lang="stylus" scoped>
  .banner
    position relative
    height 0
    padding-bottom 56.23%
    color #fff
    img
      width 100%
    .banner-info
      display flex
      align-items center
      position absolute
      height .6rem
      left 0
      right 0
      bottom 0
      padding 0 .2rem
      background-image linear-gradient(top, rgba(0,0,0,0),rgba(0,0,0,.8))
      .desc
        flex 1
      .quantity
        padding 0 .2rem
        height .4rem
        line-height .4rem
        border-radius .1rem
        background-color rgba(0,0,0,.8)
</style>
