<template>
  <div class="gallary" @click.stop="handleGallaryClick">
    <swiper  :options="swiperOption" ref="mySwiper">
      <swiper-slide v-for="item in imgs" :key="item">
        <img :src="item"/>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
  </div>
</template>
<script>
export default {
  name: 'Gallary',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  methods: {
    handleGallaryClick () {
      this.$emit('close')
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        loop: true,
        observeParents: true,
        observer: true
      }
    }
  }
}
</script>
<style lang="stylus" scoped>
  .gallary >>> .swiper-container
    width 100%
    overflow inherit
  .gallary
    position fixed
    top 0
    left 0
    right 0
    bottom 0
    background-color #000000
    display flex
    flex-direction column
    justify-content center
    img
      width 100%
    .swiper-pagination
      bottom -.6rem
</style>
