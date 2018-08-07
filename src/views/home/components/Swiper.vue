<template>
    <swiper class="swiper-wrapper" :options="swiperOption" ref="mySwiper">
      <swiper-slide v-for="item in swiperSliders" :key="item.id">
        <img class="swiper-img" :src="item.url">
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
</template>
<script>
export default {
  name: 'HomeSwiper',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      },
      swiperSliders: [
        {
          id: '001',
          url: 'https://source.qunarzz.com/site/images/wap/home/recommend/iphoneplus/dujia_shuqi_banner_20180710.jpg'
        },
        {
          id: '002',
          url: 'https://source.qunarzz.com/site/images/wap/home/recommend/iphoneplus/sc_sqdc_20180727.jpg'
        }
      ]
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
