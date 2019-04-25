
<template>
  <div>
    <div class="search">
      <input placeholder="请输入城市名或拼音" class="search-input" type="text" v-model="inputCity">
    </div>
    <div v-show="inputCity" class="search-content">
      <ul>
        <li  @click="chooseCity(item.name)" class="search-item border-bottom" v-for="item of searchList" :key="item.id">
          {{item.name}}
        </li>
        <li class="no-result" v-show="!searchList.length">搜索不到结果</li>
      </ul>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'CitySearch',
  props: {
    cities: {}
  },
  data () {
    return {
      inputCity: '',
      searchList: [],
      timer: null
    }
  },
  mounted () {
    this.scroll = new BScroll('.search-content')
  },
  watch: {
    inputCity (newVal) {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      this.timer = setTimeout(() => {
        let searchList = []
        for (let key in this.cities) {
          this.cities[key].forEach((item) => {
            if (item.name.indexOf(this.inputCity) !== -1 || item.spell.indexOf(this.inputCity) !== -1) {
              searchList.push(item)
            }
          })
        }

        this.searchList = searchList
      }, 100)
    }
  },
  methods: {
    chooseCity (city) {
      this.$store.dispatch('setCityName', city)
      this.$router.push('/')
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~mystyles/common.styl'
  .search
    background-color $bgColor
    padding .1rem
    display flex
    .search-input
      width 100%
      height .62rem
      line-height .62rem
      text-align center
      padding 0 .1rem
  .search-content
    position absolute
    top 1.68rem
    left 0
    right 0
    bottom 0
    background-color #fff
    overflow hidden
    z-index 1
    .search-item
      line-height .6rem
      height .6rem
      padding-left .2rem
    .no-result
      text-align center
      margin-top 1.25rem
      font-size 20px
</style>
