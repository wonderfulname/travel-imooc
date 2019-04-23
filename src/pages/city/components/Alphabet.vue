
<template>
  <div class="alphabet">
    <div
      @click="handleClick(item)"
      @touchstart="touchstart"
      @touchmove="touchmove"
      @touchend="touchend"
      class="item"
      v-for="item of alphaList"
      :key="item"
      :ref="item"
    >
      {{item}}
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
  computed: {
    alphaList () {
      let alphaList = []
      for (let key in this.cities) {
        alphaList.push(key)
      }

      return alphaList
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
    },
    touchmove (e) {
      // 鼠标当前位置Y坐标
      const moveKey = e.touches[0].clientY
      const distanceToA = moveKey - 84 - this.elementAY
      const indexToA = Math.floor(distanceToA / 20)
      if (indexToA > 0 && indexToA < this.alphaList.length) {
        const moveToEle = this.alphaList[indexToA]
        console.log(moveToEle)
        this.$emit('send-key', moveToEle)
      }
      // 当前坐标对应的字母
    },
    touchend (e) {
      // console.log(e)
    }
  },
  updated () {
    // const elementA = this.$refs['A']
    // console.log(elementA)
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
