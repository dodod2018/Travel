<template>
  <div>
      <city-header></city-header>
      <city-search :cities="cities.cities"></city-search>
      <city-list :letter="letter" :cities="cities"></city-list>
      <city-alphabet @letterChange="handleLetterChange" :list="cities.cities"></city-alphabet>
  </div>
</template>
<script>
import axios from 'axios'
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'
export default {
  name: 'city',
  data () {
    return {
      cities: {},
      letter: ''
    }
  },
  components: {CityHeader, CitySearch, CityList, CityAlphabet},
  methods: {
    getCityInfo () {
      axios.get('/api/city.json').then(res => {
        this.cities = res.data.data
      })
    },
    handleLetterChange (letter) {
      this.letter = letter
    }
  },
  mounted () {
    this.getCityInfo()
  }
}
</script>
