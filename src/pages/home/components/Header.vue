<template>
  <div class="header">
    <div class="back">
      <i class="iconfont icon-fanhui"></i>
    </div>
    <div class="search">
      <div class="search-input">
        <i class="iconfont icon-sousuo"></i>
        <span>输入城市/景点/游玩主题</span>
      </div>
    </div>
    <router-link to="/city" class="position">
      <span>{{city}}</span>
      <i class="iconfont icon-jiantou"></i>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'HomeHeader',
  props: {
    city: {
      type: String
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~mystyles/common.styl'
  .header
    line-height .86rem
    height .86rem
    display flex
    background-color $bgColor
    .back
      width .64rem
      text-align center
      color #fff
    .search
      flex 1
      display flex
      align-items center
      box-sizing border-box
      padding-left .1rem
      .search-input
        padding-left .1rem
        width 100%
        line-height .64rem
        border-radius .1rem
        height .64rem
        background-color #fff
        color #ccc
    .position
      box-sizing border-box
      min-width 1.28rem
      padding 0 .2rem
      text-align center
      color #fff
      font-size .2rem
      >.iconfont
        font-size .16rem
</style>
