
<template>
  <div class="search">
    <input placeholder="请输入城市名或拼音" class="search-input" type="text" v-model="inputCity">
  </div>
</template>

<script>
export default {
  name: 'CitySearch',
  data () {
    return {
      inputCity: ''
    }
  },
  methods: {
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
</style>
