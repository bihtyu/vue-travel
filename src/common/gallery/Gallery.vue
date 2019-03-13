<template>
  <div class="container" @click="handleImgClick">
    <div class="wrapper">
      <swiper :options="swiperOption">
        <swiper-slide
          v-for="(item, index) of imgs"
          :key="index"
        >
          <div class="swiper-img" :style="{backgroundImage: 'url(' + item + ')'}"></div>
        </swiper-slide>
        <div class="swiper-pagination" slot="pagination"></div>
      </swiper>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CommonGallery',
  props: {
    imgs: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        paginationType: 'fraction',
        observeParents: true,
        observer: true
      }
    }
  },
  methods: {
    handleImgClick () {
      this.$emit('closeImg')
    }
  }
}
</script>

<style scoped lang="stylus">
  .container >>> .swiper-container
    overflow: inherit
    height: 100%;
  .container
    z-index: 99
    position: absolute
    left: 0
    right: 0
    top: 0
    bottom: 0
    background: #000
    .wrapper
      position: absolute
      left: 0
      right: 0
      top: 0
      bottom: 0
      .swiper-img
        height: 100%;
        background-position: center;
        background-repeat: no-repeat;
        background-size: contain;
      .swiper-pagination
        color: #fff
</style>
