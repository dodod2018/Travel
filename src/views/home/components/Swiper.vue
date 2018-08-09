<template>
    <swiper class="swiper-wrapper" :options="swiperOption" ref="mySwiper">
      <swiper-slide v-for="item in list" :key="item.id">
        <img class="swiper-img" :src="item.imgUrl">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
</template>
<script>
export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      }
    }
  }
}
</script>
<style lang="stylus" scoped>
  .swiper-wrapper >>> .swiper-pagination-bullet-active
    background-color #fff
  .swiper-wrapper
    width 100%
    height 0
    padding-bottom 24.5%
    overflow hidden
    background-color #eee
  .swiper-img
    width 100%
</style>
