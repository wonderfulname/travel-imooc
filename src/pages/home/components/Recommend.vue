<template>
    <div class="recommend">
      <div class="recommend-title">热销推荐</div>
      <ul class="recommend-list">
        <router-link tag="li"
          class="border-bottom"
          v-for="(item, index) of recommendList"
          :key="index"
          :to="`/detail/${item.id}`"
        >
          <img :src="item.imgUrl" alt="">
          <div class="item-info">
            <div class="title">{{item.title}}</div>
            <div class="description">{{item.desc}}</div>
            <div class="detail">查看详情</div>
          </div>
        </router-link>
      </ul>
    </div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    recommendList: Array
  },
  data () {
    return {
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
