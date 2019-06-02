<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" :src="bannerImg">
      <div class="banner-info">
        <div class="banner-title">{{this.sightName}}</div>
        <div class="banner-number">{{this.bannerImgs.length}}</div>
      </div>
    </div>
    <common-fade>
      <common-gallary :imgs="bannerImgs" v-show="showGallary" @close="handleGalleryClose"></common-gallary>
    </common-fade>
  </div>

</template>

<script>
import CommonGallary from 'common/gallary/Gallary'
import CommonFade from 'common/fade/FadeAnimation'
export default {
  name: 'DetailBanner',
  components: {
    CommonGallary,
    CommonFade
  },
  props: {
    sightName: String,
    bannerImg: String,
    bannerImgs: Array
  },
  data () {
    return {
      showGallary: false
    }
  },
  methods: {
    handleGalleryClose () {
      this.showGallary = false
    },
    handleBannerClick () {
      this.showGallary = true
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
      display flex
      position absolute
      left 0
      right 0
      bottom 0
      line-height .6rem
      color #fff
      .banner-title
        flex 1
        font-size .32rem
        padding 0 0.2rem
      .banner-number
        height: .32rem
        line-height: .32rem
        margin-top: .14rem
        padding: 0 .4rem
        border-radius: .2rem
        background: rgba(0, 0, 0, .8)
        font-size: .24rem
</style>
