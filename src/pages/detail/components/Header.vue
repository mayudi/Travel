<template>
  <div>
    <router-link
      tag="div"
      to="/"
      class="header-abs"
      v-show="showAbs">
      <div class="iconfont header-abs-back">&#xe624;</div>
    </router-link>
    <div
      class="header-fixed"
      v-show="!showAbs"
      :style="opacityStyle"
    >
      <router-link to="/">
        <div class="iconfont header-fixed-back">&#xe624;</div>
      </router-link>
      景点详情
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {opacity}
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handleScroll)
  },
  updated () {
    window.addEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl'
  .header-abs
    position absolute
    left .2rem
    top .2rem
    width .8rem
    height .8rem
    background rgb(0,0,0,.8)
    border-radius .4rem
    line-height .8rem
    text-align center
    .header-abs-back
      color #fff
      font-size .4rem
  .header-fixed
    z-index: 2
    position fixed
    top 0
    left 0
    right 0
    height $headerHeight
    line-height $headerHeight
    background $bgColor
    color #fff
    font-size .32rem
    text-align: center
    .header-fixed-back
      position absolute
      left 0
      top 0
      color #fff
      font-size .4rem
      width .64rem

</style>
