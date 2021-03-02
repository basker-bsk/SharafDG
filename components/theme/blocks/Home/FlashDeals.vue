
<template>
<div>
  <swiper class="swiper" :options="swiperOption">
    <swiper-slide>
        <div class="d-flex flex-column">
            <p><img alt="" class="m-auto tile-product__img w-xs-140 w-md-250" src="https://changiairport.scene7.com/is/image/changiairport/sk-ii-sk-ii-facial-treatment-essence-deluxe-duo-set-mp00051337-1"></p>

        </div>
    </swiper-slide>
    <swiper-slide>Slide 2</swiper-slide>
    <swiper-slide>Slide 3</swiper-slide>
    <swiper-slide>Slide 4</swiper-slide>
    <swiper-slide>Slide 5</swiper-slide>
    <swiper-slide>Slide 6</swiper-slide>
    <swiper-slide>Slide 7</swiper-slide>
    <swiper-slide>Slide 8</swiper-slide>
    <swiper-slide>Slide 9</swiper-slide>
    <swiper-slide>Slide 10</swiper-slide>
    <div class="swiper-scrollbar" slot="scrollbar"></div>
    <div class="swiper-button-prev" slot="button-prev"></div>
    <div class="swiper-button-next" slot="button-next"></div>
  </swiper>
  </div>
</template>

<script>
  import { Swiper, SwiperSlide} from 'vue-awesome-swiper'
  import 'swiper/swiper.min.css'
  
  export default {
    name: 'FlashDeals',
    title: 'Scrollbar',
    components: {
      Swiper,
      SwiperSlide
    },
    data() {
      return {
        swiperOption: {
          slidesPerView: 4,
          spaceBetween: 30,
          scrollbar: {
            el: '.swiper-scrollbar',
            hide: false
          },
          navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev'
          }
        }
      }
    },
     
  }
</script>

<style lang="scss" scoped>
  .swiper {
  height: 300px;
  width: 100%;

  .swiper-slide {
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-weight: bold;
    font-size: 14px;
    background-color:#fff;
  }
}
</style>