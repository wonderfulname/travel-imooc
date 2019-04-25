
<template>
  <div class="list">
    <div>
      <div class="area">
        <div class="title">当前城市</div>
        <div class="button-list">
          <div class="item-wrapper">
            <div class="button-item">{{city}}</div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title">热门城市</div>
        <div class="button-list">
          <div class="item-wrapper" v-for="item of hotCities" :key="item.id">
            <div @click="chooseCity(item.name)" class="button-item">{{item.name}}</div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(value, key) of cities" :key="key" :ref="key">
        <div class="title">{{key}}</div>
        <div class="item-list">
          <div @click="chooseCity(item.name)" class="item border-bottom" v-for="item of value" :key="item.id">{{item.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import BScroll from 'better-scroll'
export default {
  name: 'CityList',
  props: {
    alphKey: {
      type: String
    },
    cities: Object,
    hotCities: Array
  },
  data () {
    return {
    }
  },
  computed: {
    city () {
      return this.$store.state.city
    }
  },
  mounted () {
    this.scroll = new BScroll('.list')
  },
  watch: {
    alphKey (newVal) {
      if (this.alphKey) {
        this.scroll.scrollToElement(this.$refs[newVal][0])
      }
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
  .border-bottom
    &::after
      border-color #aaa
  .list
    position absolute
    overflow hidden
    left 0
    top 1.68rem
    bottom 0
    right 0
    .area
      .title
        height .54rem
        line-height .54rem
        background-color #eee
        color #666
        text-indent .2rem
      .button-list
        padding .1rem .6rem .1rem .2rem
        display flex
        flex-wrap wrap
        .item-wrapper
          width 33.33%
          .button-item
            box-sizing border-box
            height .6rem
            line-height .6rem
            text-align center
            border 1px solid #ccc
            margin .1rem .1rem
            border-radius 4px
      .item-list
        .item
          line-height .6rem
          height .6rem
          text-indent .2rem
</style>
