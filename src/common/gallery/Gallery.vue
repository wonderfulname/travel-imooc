<template>
  <div class="container" @click="hideGallery">
    <div class="wraper">
      <swiper :options="swiperOption">
        <!-- slides -->
        <swiper-slide v-for="item of swiperList" :key="item.id">
          <img class="swiper-img" :src="item.imgUrl" alt="">
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallery',
  props: {
    swiperList: {
      type: Array,
      default () {
        return [
          {
            imgUrl: 'http://img1.qunarzz.com/sight/p0/1802/47/47d11c826e75e0ea3.img.jpg_r_800x800_2df5e7a2.jpg',
            id: '0001'
          },
          {
            imgUrl: 'http://img1.qunarzz.com/sight/p0/1802/78/787c3d707913f8ea3.img.jpg_r_800x800_b90570c5.jpg',
            id: '0002'
          }
        ]
      }
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observer: true,
        observeParents: true
      }
    }
  },
  methods: {
    hideGallery () {
      this.$emit('hideGallery')
    }
  }
}
</script>

<style lang="stylus" scoped>
  .container
    position fixed
    top 0
    left 0
    right 0
    bottom 0
    background-color #000
    display flex
    flex-direction column
    color #fff
    justify-content center
    .wraper
      height 100%
      // background-color red
      .swiper-container
        height: 100%
        .swiper-slide
          display flex
          align-items center
          .swiper-img
            width 100%
        .swiper-pagination-fraction
          bottom 50px
</style>
