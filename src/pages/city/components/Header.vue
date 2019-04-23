<template>
  <div class="header">
    <router-link to="/" class="back">
      <i class="iconfont icon-fanhui"></i>
    </router-link>
    城市选择
  </div>
</template>

<script>
export default {
  name: 'CityHeader',
  data () {
    return {
    }
  },
  methods: {
  }
}
</script>

<style lang="stylus" scoped>
  @import '~mystyles/common.styl'
  .header
    text-align center
    height .86rem
    line-height .86rem
    position relative
    background-color $bgColor
    color #fff
    .back
      position absolute
      left .2rem
      color #fff
</style>
