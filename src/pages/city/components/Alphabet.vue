
<template>
  <div class="alphabet">
    <div
      @click="handleClick(key)"
      @touchstart="touchstart"
      @touchmove="touchmove"
      @touchend="touchend"
      class="item"
      v-for="(value, key) of cities"
      :key="key"
      :ref="key"
    >
      {{key}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'CityAlphabet',
  props: {
    cities: Object
  },
  data () {
    return {
      elementAY: 0
    }
  },
  methods: {
    handleClick (key) {
      // console.log(key)
      this.$emit('send-key', key)
    },
    touchstart (e) {
      const elementAY = this.$refs['A'][0].offsetTop
      console.log(elementAY)
      this.elementAY = elementAY
      // console.log(e)
    },
    touchmove (e) {
      // console.log(e)
      const moveKey = e.touches[0].clientY
      // console.log(moveKey)
      const distanceToA = moveKey - 84 - this.elementAY
      console.log(distanceToA)
    },
    touchend (e) {
      // console.log(e)
    },
    updated () {
      // const elementA = this.$refs['A']
      // console.log(elementA)
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~mystyles/common.styl'
  .alphabet
    position absolute
    top 1.68rem
    bottom 0
    right 0
    // background-color red
    width 30px
    display flex
    flex-direction column
    justify-content center
    align-items center
    .item
      line-height .4rem
      color $bgColor
</style>
