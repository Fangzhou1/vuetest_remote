<template>
<div>
  <div if-show="this.images.length" class="swiper-container" >
    <div  class="swiper-wrapper">
      <div v-for="(item,index) in images" class="swiper-slide" :key="index"><img :src="item.imageurl" /></div>
    </div>
    <!-- 如果需要分页器 -->
    <div class="swiper-pagination"></div>
    <!-- 如果需要导航按钮 -->
    <div class="swiper-button-prev"></div>
    <div class="swiper-button-next"></div>

  </div>
</div>
</template>

<script>
import Swiper from 'swiper'
export default {
  data() {
    return {
      msg: 'Welcome to Your Vue.js App',

    }
  },
  props: {
    images: {
      type: Array,
      default () {
        return []
      }
    }
  },

  mounted() {
this.timer=setTimeout(function(){new Swiper('.swiper-container', {
 loop: true,
 autoplay: true,
 effect: 'fade',
 // 如果需要分页器
 pagination: {
   el: '.swiper-pagination'
 },
 // 如果需要前进后退按钮
 navigation: {
   nextEl: '.swiper-button-next',
   prevEl: '.swiper-button-prev'
 }
})},200)


  },
  methods: {

  },
  destroyed() {
    clearTimeout(timer);
  }
}
</script>

<style lang="scss" scoped>
@import 'swiper/dist/css/swiper.css';
.swiper-container {
    width: 80%;
    img {
        width: 100%;
        text-align: center;

    }
}
</style>
