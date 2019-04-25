<template>
  <div>
    <home-header></home-header>
    <home-swiper :swiperList="swiperList"></home-swiper>
    <home-icons :iconsList="iconsList"></home-icons>
    <home-recommend :recommendList="recommendList"></home-recommend>
  </div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from './components/Icons'
import HomeRecommend from './components/Recommend'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend
  },
  data () {
    return {
      swiperList: [],
      iconsList: [],
      recommendList: []
    }
  },
  mounted () {
    this.getHomeInfo()
    console.log(this.city)
    console.log('mounted')
    this.lastCity = this.city
  },
  activated () {
    console.log('activated')
    console.log(this.city)
    if (this.city !== this.lastCity) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  },
  computed: {
    city: {
      get () {
        return this.$store.state.city
      },
      set: function (newValue) {
        this.$store.state.city = newValue
      }
    }
  },
  methods: {
    getHomeInfo () {
      axios.get('/api/index.json?city=' + this.city)
        .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      console.log(res)
      if (res.data.ret && res.data.data) {
        const data = res.data.data
        this.city = data.city
        this.swiperList = data.swiperList
        this.iconsList = data.iconList
        this.recommendList = data.recommendList
      }
    }
  }
}
</script>

<style lang="stylus" scoped>

</style>
