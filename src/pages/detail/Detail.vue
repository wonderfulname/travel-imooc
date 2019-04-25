<template>
  <div>
    <detail-banner></detail-banner>
  </div>
</template>

<script>
import DetailBanner from './components/banner'
export default {
  name: 'Detail',
  components: {
    DetailBanner
  },
  data () {
    return {
    }
  },
  mounted () {
    this.paraId = this.$route.params.id
    console.log(this.paraId)
  },
  methods: {
  }
}
</script>

<style lang="stylus" scoped>
</style>
