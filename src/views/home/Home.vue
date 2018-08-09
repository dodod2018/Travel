<template>
    <div>
        <home-header/>
        <home-swiper :list="swiperList"/>
        <home-icons :list="iconList"/>
        <home-recommend :list="recommendList"/>
        <home-weekend :list="weekendList"/>
    </div>
</template>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import { mapState } from 'vuex'
export default {
  name: 'home',
  data () {
    return {
      swiperList: [],
      recommendList: [],
      iconList: [],
      weekendList: [],
      lastCity: ''
    }
  },
  computed: {
    ...mapState(['city'])
  },
  components: {HomeHeader, HomeSwiper, HomeIcons, HomeRecommend, HomeWeekend},
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json').then((res) => {
        const {swiperList, recommendList, iconList, weekendList} = res.data.data
        this.swiperList = swiperList
        this.recommendList = recommendList
        this.iconList = iconList
        this.weekendList = weekendList
      })
    }
  },
  mounted () {
    this.getHomeInfo()
    this.lastCity = this.city
  },
  activated () {
    if (this.lastCity !== this.city) {
      this.getHomeInfo()
    }
  }
}
</script>
