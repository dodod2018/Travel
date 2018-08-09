<template>
  <div class="search">
    <input v-model="keyword" type="text" placeholder="输入城市名或拼音">
    <div v-show="keyword" class="search-list" ref="wrapper">
      <ul>
        <li class="border-bottom" v-for="item in list" :key="item.id">{{item.name}}</li>
        <li v-show="!list.length">找不到匹配项</li>
      </ul>
    </div>
  </div>
</template>
<script>
import BScroll from 'better-scroll'
export default {
  name: 'citySearch',
  props: {
    cities: Object
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
  },
  data () {
    return {
      list: [],
      keyword: '',
      timer: null
    }
  },
  watch: {
    keyword () {
      this.list = []
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        for (let i in this.cities) {
          this.cities[i].forEach(item => {
            if (item.spell.indexOf(this.keyword) !== -1 || item.name.indexOf(this.keyword) !== -1) {
              this.list.push(item)
            }
          })
        }
      }, 100)
    }
  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles.styl'
  .search
    height.72rem
    background-color $bgColor
    padding 0 .1rem
    input
      width 100%
      height .62rem
      line-height .62rem
      text-align center
      border-radius .06rem
      padding 0 .2rem
      box-sizing border-box
      color #666
    .search-list
      position: absolute
      bottom: 0
      left: 0
      right: 0
      top: 1.58rem
      z-index: 1
      overflow: hidden
      background-color: #eee
      li
        background-color #fff
        line-height .6rem
        height .6rem
        text-indent .2rem
</style>
