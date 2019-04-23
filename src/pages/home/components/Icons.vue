<template>
    <swiper :options="swiperOption">
      <!-- slides -->
      <swiper-slide v-for="(item, index) of devideList" :key="item.id">
        <div class="icons">
          <div class="icons-item" v-for="itemChild of devideList[index]" :key="itemChild.id">
            <img :src="itemChild.imgUrl" alt="">
            <div>{{itemChild.desc}}</div>
          </div>
        </div>
      </swiper-slide>
      <!-- Optional controls -->
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>
</template>

<script>
export default {
  name: 'HomeIcons',
  props: {
    iconsList: Array
  },
  data () {
    return {
      //  轮播配置
      swiperOption: {
        autoplay: 3000,
        pagination: '.swiper-pagination'
      }
    }
  },
  computed: {
    devideList () {
      let devideList = []
      this.iconsList.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!devideList[page]) {
          devideList[page] = []
        }
        devideList[page].push(item)
      })

      return devideList
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~mystyles/mixins.styl'
  .icons
    padding-top 10px
    padding-bottom 190px
    height 0
    overflow hidden
    display flex
    flex-wrap wrap
    .icons-item:first-child()
      margin-top 10px
    .icons-item
      width 25%
      height 80px
      display flex
      flex-direction column
      align-items center
      justify-content space-around
      >img
        width 55px
        height 55px
      >div
        width 100%
        text-align center
        ellipsis()
</style>
