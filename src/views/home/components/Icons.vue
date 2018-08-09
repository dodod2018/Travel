<template>
  <div class="icon-area">
    <div class="icon-wrapper">
    <div class="icon-item-wrapper">
      <swiper :options="swiperOption" class="swiper-wrapper">
        <swiper-slide v-for="(page,index) in pages" :key="index">
          <div class="icon-item" v-for="item in page" :key="item.id">
            <div class="icon-img-wrapper">
              <img :src="item.imgUrl" alt="">
            </div>
            <p>{{item.desc}}</p>
          </div>
        </swiper-slide>
      </swiper>
    </div>
  </div>
  </div>
</template>
<script>
export default {
  name: 'HomeIcons',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      let pages = {}
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
  .icon-area
    margin-top .1rem
    margin-bottom .2rem
  .icon-wrapper
    width 100%
    height 0
    overflow hidden
    padding-bottom 40%
    position relative
    .icon-item-wrapper
      position absolute
      left 0
      top 0
      right 0
      bottom 0
      .icon-item
        float left
        width 25%
        height 50%
        overflow hidden
        position relative
        p
          position absolute
          bottom 0
          height .44rem
          line-height .44rem
          width 100%
          text-align center
          color $darkTextColor
        .icon-img-wrapper
          position absolute
          left 0
          right 0
          top .2rem
          bottom .44rem
          text-align center
          img{
            height 100%
            margin 0 auto
          }
</style>
