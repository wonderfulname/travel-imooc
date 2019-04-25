<template>
  <div>
    <div class="banner">
      <img @click="showGallery" class="banner-img" src="//img1.qunarzz.com/sight/p0/1607/21/2142167d4b1bfa84b4.water.jpg_600x330_be3593ab.jpg" alt="">
      <div class="banner-info">
        <div>西塘古镇(AAAAA景区)</div>
        <div>
          <i class="iconfont icon-image"></i>
          <span>39</span>
        </div>
      </div>
    </div>
    <common-gallery v-show="isShowGallery" @hideGallery="hideGallery" :swiperList="swiperList"></common-gallery>
  </div>
</template>

<script>
import CommonGallery from 'mycommon/gallery/Gallery'
export default {
  name: 'Banner',
  components: {
    CommonGallery
  },
  data () {
    return {
      isShowGallery: false,
      swiperList: [
        {
          imgUrl: 'http://img1.qunarzz.com/sight/p0/1802/47/47d11c826e75e0ea3.img.jpg_r_800x800_2df5e7a2.jpg',
          id: '0001'
        },
        {
          imgUrl: 'http://img1.qunarzz.com/sight/p0/1802/78/787c3d707913f8ea3.img.jpg_r_800x800_b90570c5.jpg',
          id: '0002'
        },
        {
          imgUrl: 'http://img1.qunarzz.com/sight/p0/1802/26/26577663bf5179caa3.img.jpg_r_800x800_8444d381.jpg',
          id: '0003'
        },
        {
          imgUrl: 'http://img1.qunarzz.com/sight/p0/1802/8f/8f55ff201702f8b9a3.img.jpg_r_800x800_217a0e4a.jpg',
          id: '0004'
        }
      ]
    }
  },
  methods: {
    // 点击当前图片 展示banner列表
    showGallery () {
      this.isShowGallery = true
    },
    // 监听gallery事件 隐藏gallery
    hideGallery () {
      this.isShowGallery = false
    }
  }
}
</script>

<style lang="stylus" scoped>
  .banner
    position relative
    overflow hidden
    height 0
    padding-bottom 55%
    .banner-img
      width 100%
    .banner-info
      position absolute
      bottom 0
      left 0
      right 0
      color #fff
      display flex
      // background-color blue
      height 30px
      align-items center
      justify-content space-between
      padding 0 20px
</style>
