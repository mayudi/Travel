<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" src="bannerImg">
      <div class="banner-info">
        <div class="banner-title">{{this.sightName}}</div>
        <div class="banner-number">{{this.bannerImgs.length}}</div>
      </div>
    </div>
    <common-gallary :imgs="bannerImgs" v-show="showGallary" @close="handleGalleryClose"></common-gallary>
  </div>

</template>

<script>
  import CommonGallary from 'common/gallery/Gallery'

  export default {
    name: "DetailBanner",
    comments: {
      CommonGallary
    },
    props: {
      sightName: String,
      bannerImg: String,
      bannerImgs: Array
    },
    data() {
      return {
        showGallary: false
      }
    },
    methods: {
      handleGalleryClose() {
        this.showGallary = false
      },
      handleBannerClick() {
        this.showGallary = true
      }
    }
  }
</script>

<style scoped>

</style>
