<template>
  <div>
    <city-header></city-header>
    <city-search></city-search>
    <city-list :alphKey="alphKey" :cities="cities" :hotCities="hotCities"></city-list>
    <city-alphabet @send-key="getKey" :cities="cities"></city-alphabet>
  </div>
</template>

<script>
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
  },
  data () {
    return {
      cities: {},
      hotCities: [],
      alphKey: ''
    }
  },
  methods: {
    getCityInfo () {
      axios.get('/api/city.json')
        .then(this.getCityInfoSucc)
    },
    getCityInfoSucc (res) {
      console.log(res)
      if (res.data.ret && res.data.data) {
        const data = res.data.data
        this.cities = data.cities
        this.hotCities = data.hotCities
      }
    },
    getKey (key) {
      console.log(key)
      this.alphKey = key
    }
  },
  mounted () {
    this.getCityInfo()
  }
}
</script>

<style lang="stylus" scoped>

</style>
