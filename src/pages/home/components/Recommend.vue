<template>
    <div class="recommend">
      <div class="recommend-title">热销推荐</div>
      <ul class="recommend-list">
        <li class="border-bottom" v-for="(item, index) of showList" :key="index">
          <img :src="item.imgSrc" alt="">
          <div class="item-info">
            <div class="title">{{item.title}}</div>
            <div class="description">{{item.description}}</div>
            <div class="detail">查看详情</div>
          </div>
        </li>
      </ul>
    </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  data () {
    return {
      showList: [
        {
          imgSrc: 'http://img1.qunarzz.com/sight/p0/1604/1e/1e75f8e1af9fe81f90.img.jpg_200x200_0ded2b1b.jpg',
          title: '世界花卉大观园世界花卉大观园世界花卉大观园',
          description: '六点四个不具有回家吧六点四个不具有回家吧六点四个不具有回家吧六点四个不具有回家吧'
        },
        {
          imgSrc: 'http://img1.qunarzz.com/sight/p0/1604/1e/1e75f8e1af9fe81f90.img.jpg_200x200_0ded2b1b.jpg',
          title: '世界花卉大观园',
          description: '六点四个不具有回家吧'
        },
        {
          imgSrc: 'http://img1.qunarzz.com/sight/p0/1604/1e/1e75f8e1af9fe81f90.img.jpg_200x200_0ded2b1b.jpg',
          title: '世界花卉大观园',
          description: '六点四个不具有回家吧'
        },
        {
          imgSrc: 'http://img1.qunarzz.com/sight/p0/1604/1e/1e75f8e1af9fe81f90.img.jpg_200x200_0ded2b1b.jpg',
          title: '世界花卉大观园',
          description: '六点四个不具有回家吧'
        }
      ]
    }
  }
}
</script>

<style lang="stylus" scoped>
  @import '~mystyles/mixins.styl'
  .recommend
    .recommend-title
      height 40px
      line-height 40px
      background-color #eee
      text-indent 2em
    .recommend-list > li
      box-sizing border-box
      padding .1rem
      display flex
      >img
        width 85px
        height 85px
        margin-right .2rem
      .item-info
        flex 1
        min-width 0
        .title
          height 24px
          line-height 24px
          font-size 18px
          margin-top 4px
          ellipsis()
        .description
          margin-top 6px
          color #ccc
          ellipsis()
        .detail
          background-color #ff5500
          width 80px
          height 24px
          text-align center
          line-height 24px
          margin-top 4px
          border-radius 4px
          color #fff
</style>
