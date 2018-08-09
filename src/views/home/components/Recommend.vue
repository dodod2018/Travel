<template>
  <div>
    <div class="recommend-title">热销推荐</div>
    <ul class="recommend-list">
      <li v-for="item in list" :key="item.id" class="recommend-item border-bottom">
        <img :src="item.imgUrl">
        <div class="recommend-info">
          <p class="recommend-info-title">{{item.title}}</p>
          <p class="recommend-info-address">{{item.desc}}</p>
          <button @click="gotoDetail(item.id)">查看详情</button>
        </div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  name: 'HomeRecommend',
  props: {
    list: Array
  },
  data () {
    return {
    }
  },
  methods: {
    gotoDetail (id) {
      this.$router.push('/detail/' + id)
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
      display flex
      padding .2rem
      img
        width 2rem
        height 2rem
      .recommend-info
        flex 1
        display: flex
        flex-direction: column
        justify-content: space-between
        margin-left: .2rem
        .recommend-info-title
          font-weight bold
        .recommend-info-address
          font-size .24rem
          color #333
        button
          display inline-block
          background-color #FF9C30
          padding .1rem .32rem
          color #fff
          align-self flex-start
</style>
