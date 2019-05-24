<template>
  <div>
    <div class="banner">
      <img class="banner-img" src="bannerImg">
      <div class="banner-info">
        <div class="banner-title">{{this.sightName}}</div>
        <div class="banner-number">{{this.bannerImgs.length}}</div>
      </div>
    </div>
  </div>

</template>

<script>
  export default {
    name: "DetailBanner",
    props: {
      sightName: String,
      bannerImg: String,
      bannerImgs: Array
    }
  }
</script>

<style scoped>

</style>
