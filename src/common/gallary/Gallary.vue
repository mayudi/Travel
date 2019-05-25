<template>
    <div class="container" @click="handleGalleryClick">
      <div class="wrapper" >
        <swiper :options="swiperOptions">
          <swiper-slide v-for="(item ,index) in imgs" :key="index">
            <img :src="item" class="gallary-img">
          </swiper-slide>
          <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
      </div>
    </div>
</template>

<script>
    export default {
      name: "CommonGallary",
      props: {
        imgs: {
          type:Array,
          default() {
            return []
          }
        }
      },
      data () {
        return {
          swiperOptions: {
            pagination: '.swiper-pagination',
            paginationType: 'fraction',
            observeParents: true,
            observer: true
          }
        }
      },
      methods: {
        handleGalleryClick(){
          this.$emit('close')
        }
      }
    }
</script>

<style scoped>

</style>
