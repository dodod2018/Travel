<template>
  <div class="list-container" ref="wrapper">
    <div >
      <div class="block">
        <p class="block-title">当前城市</p>
        <ul class="block-list">
          <li @click="changeCity(this.$store.state.city)">{{this.$store.state.city}}</li>
        </ul>
      </div>
      <div class="block">
        <p class="block-title">热门城市</p>
        <ul class="block-list">
          <li v-for="item in cities.hotCities" :key="item.id" @click="changeCity(item.name)">{{item.name}}</li>
        </ul>
      </div>
      <div class="block" v-for="(value,key) in cities.cities" :key="key" :ref="key">
        <p class="block-title">{{key.toUpperCase()}}</p>
        <ul class="block-list">
          <li v-for="city in value" :key="city.id" @click="changeCity(city.name)">{{city.name}}</li>
        </ul>
      </div>
    </div>
  </div>
</template>
<script>
import BScroll from 'better-scroll'
export default {
  name: 'CityList',
  props: {
    cities: Object,
    letter: String
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.wrapper)
  },
  methods: {
    changeCity (city) {
      this.$store.dispatch('changeCity', city)
      this.$router.push('/')
    }
  },
  watch: {
    letter () {
      this.scroll.scrollToElement(this.$refs[this.letter][0])
    }
  }
}
</script>
<style lang="stylus" scoped>
.list-container {
  background-color: #eee;
  position: absolute;
  top: 1.58rem;
  bottom: 0;
  left: 0;
  right: 0;
  padding: 0 0.6rem 0 0.2rem;
  overflow: hidden;

  .block-title {
    font-size: 0.24rem;
    line-height: 0.64rem;
    height: 0.64rem;
    color: #827a7a;
  }

  .block-list {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;

    li {
      width: 30%;
      height: 0.64rem;
      line-height: 0.64rem;
      background-color: #fff;
      text-align: center;
      white-space: nowrap;
      text-overflow: ellipsis;
      overflow: hidden;
      margin-bottom: 4%;
      box-sizing border-box
      padding 0 .1rem
    }
  }
}
</style>
