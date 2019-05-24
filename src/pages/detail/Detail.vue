<template>
  <detail-banner
    :sightName="sightName"
    :bannerImg="bannerImg"
    :bannerImgs="gallaryImgs"
  ></detail-banner>
</template>

<script>
  import axios from 'axios'
  import DetailBanner from './Banner'

  export default {
    name: "Detail",
    components: {
      DetailBanner
    },
    data() {
      return {
        sightName: '',
        bannerImg: '',
        gallaryImgs: [],
        list: []
      }
    },
    methods: {
      getDetailInfo() {
        axios.get('./detail.json', {
          params: {
            id: this.$route.params.id
          }
        }).then(this.handleGetDataSucc)
      },
      handleGetDataSucc(res) {
        res = res.data;
        if (res.res && res.data) {
          const data = res.data;
          this.sightName = data.sightName;
          this.bannerImg = data.bannerImg;
          this.gallaryImgs = data.gallaryImgs;
          this.list = data.categoryList;
        }


      }
    },
    mounted() {
      this.getDetailInfo()
    }
  }
</script>

<style scoped>

</style>
