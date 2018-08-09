<template>
  <div>
    <div class="recommend-title">周末去哪儿</div>
    <ul class="recommend-list">
      <li v-for="item in list" :key="item.id" class="recommend-item border-bottom">
        <img :src="item.imgUrl">
        <div class="recommend-info">
          <p class="recommend-info-title">{{item.title}}</p>
          <p class="recommend-info-desc">{{item.desc}}</p>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'HomeWeekend',
  props: {
    list: Array
  },
  data () {
    return {
    }
  }
}
</script>
<style lang="stylus" scoped>
  .recommend-title
    height .6rem
    line-height .6rem
    background-color #eee
    text-indent .2rem
  .recommend-list
    .recommend-item
      padding-bottom .2rem
      img
        width 100%
      .recommend-info
        display: flex
        flex-direction: column
        justify-content: space-between
        margin-left: .2rem
        .recommend-info-title
          font-weight bold
          height .64rem
          line-height .64rem
        .recommend-info.desc
          font-size .2rem
          color #eee
</style>
