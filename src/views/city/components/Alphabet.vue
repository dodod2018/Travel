<template>
  <ul class="list">
    <li v-for="item in letters" :key="item" :ref="item"
      @click="handleLetterClick(item)"
      @touchstart="handleTouchStart"
      @touchmove="handleTouchMove"
      @touchend="handleTouchEnd"
    >{{item}}</li>
  </ul>
</template>
<script>
export default {
  name: 'CityAlphabet',
  props: {
    list: Object
  },
  data () {
    return {
      touchStatus: false,
      startY: 0,
      timer: null
    }
  },
  updated () {
    this.startY = this.$refs['A'][0].offsetTop
  },
  computed: {
    letters () {
      let ary = []
      for (const i in this.list) {
        ary.push(i)
      }
      return ary
    }
  },
  methods: {
    handleLetterClick (letter) {
      this.$emit('letterChange', letter)
    },
    handleTouchMove (e) {
      if (this.touchStatus) {
        if (this.timer) {
          clearTimeout(this.timer)
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY
          const index = Math.floor((touchY - this.startY - 79) / 19)
          if (index >= 0 && index < this.letters.length) {
            this.$emit('letterChange', this.letters[index])
          }
        }, 16)
      }
    },
    handleTouchStart () {
      this.touchStatus = true
    },
    handleTouchEnd () {
      this.touchStatus = false
    }

  }
}
</script>
<style lang="stylus" scoped>
@import '~styles/varibles'
  .list
    position absolute
    top 1.58rem
    bottom 0
    right 0
    display flex
    flex-direction column
    justify-content center
    color $bgColor
    li
      line-height 1.2em
      text-align: center;
      width: .5rem;
      font-size: .32rem;
</style>
