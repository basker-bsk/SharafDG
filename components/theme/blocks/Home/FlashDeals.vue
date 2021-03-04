<template>
  <div class="swiper-products-wrapper container">
    <div class="section-title my-md-30 d-xs-flex justify-flex-start">
        <div class="d-xs-flex align-content-center">
          <h5>
                {{ $t('Flash Deals') }}
          </h5>
          <span class="timer px10 py-xs-3 ml15">18:35:10</span>
        </div>
        <div class="view-all text-right"> <a href="#">See All Deals ></a></div>
      </div>
    <swiper class="swiper" :options="swiperOption">
      <swiper-slide class="d-xs-flex align-item-center swiper-tile-products-carousel">
        <div class="overflow-hidden relative py-xs-30 tile-product"> 
              <span class="tile-product__latest absolute"> New </span>
              <span class="absolute tile-product__wishlist"> 
                <Icon icon-id="wishlist" class="icon-wishlist"></Icon>          
              </span>
              <img alt="" class="m-auto tile-product__img" src="https://changiairport.scene7.com/is/image/changiairport/sk-ii-sk-ii-facial-treatment-essence-deluxe-duo-set-mp00051337-1"> 
              <p class="tile-product__promo">  
                  20% Off
              </p>
              <div> 
                  <p class="tile-product__name"> Hugo Boss Femme Women EDP 30ml</p>
                  <div class="tile-product__rating my-xs-10">  
                    <span>* * * * * 120</span> 
                  </div>
                  <p class="tile-product__price"> 
                      <span class="discounted"> AED 2,695.00 </span> 
                      <span class="actual"> AED 2,850.00 </span> 
                  </p>
                  <p class="tile-product__pickup">Immediate Pickup</p>
                  <p class="tile-product__options">4 Options</p>
              </div>
        </div> 
      </swiper-slide>

      <swiper-slide class="d-xs-flex align-item-center swiper-tile-products-carousel">
        <div class="overflow-hidden relative py-xs-30 tile-product"> 
              <span class="tile-product__latest absolute"> SLIDE-2 </span>
              <span class="absolute tile-product__wishlist"> 
                <Icon icon-id="wishlist" class="icon-wishlist"></Icon>          
              </span>
              <img alt="" class="m-auto tile-product__img" src="https://changiairport.scene7.com/is/image/changiairport/sk-ii-sk-ii-facial-treatment-essence-deluxe-duo-set-mp00051337-1"> 
              <p class="tile-product__promo">  
                  20% Off
              </p>
              <div> 
                  <p class="tile-product__name"> Hugo Boss Femme Women EDP 30ml</p>
                  <div class="tile-product__rating my-xs-10">  
                    <span>* * * * * 120</span> 
                  </div>
                  <p class="tile-product__price"> 
                      <span class="discounted"> AED 2,695.00 </span> 
                      <span class="actual"> AED 2,850.00 </span> 
                  </p>
                  <p class="tile-product__pickup">Immediate Pickup</p>
                  <p class="tile-product__options">4 Options</p>
              </div>
        </div> 
      </swiper-slide>

      <swiper-slide class="d-xs-flex align-item-center swiper-tile-products-carousel">
        <div class="overflow-hidden relative py-xs-30 tile-product"> 
              <span class="tile-product__latest absolute"> SLIDE-3 </span>
              <span class="absolute tile-product__wishlist"> 
                <Icon icon-id="wishlist" class="icon-wishlist"></Icon>          
              </span>
              <img alt="" class="m-auto tile-product__img" src="https://changiairport.scene7.com/is/image/changiairport/sk-ii-sk-ii-facial-treatment-essence-deluxe-duo-set-mp00051337-1"> 
              <p class="tile-product__promo">  
                  20% Off
              </p>
              <div> 
                  <p class="tile-product__name"> Hugo Boss Femme Women EDP 30ml</p>
                  <div class="tile-product__rating my-xs-10">  
                    <span>* * * * * 120</span> 
                  </div>
                  <p class="tile-product__price"> 
                      <span class="discounted"> AED 2,695.00 </span> 
                      <span class="actual"> AED 2,850.00 </span> 
                  </p>
                  <p class="tile-product__pickup">Immediate Pickup</p>
                  <p class="tile-product__options">4 Options</p>
              </div>
        </div> 
      </swiper-slide>

      <swiper-slide class="d-xs-flex align-item-center swiper-tile-products-carousel">
        <div class="overflow-hidden relative py-xs-30 tile-product"> 
              <span class="tile-product__latest absolute"> SLIDE-4 </span>
              <span class="absolute tile-product__wishlist"> 
                <Icon icon-id="wishlist" class="icon-wishlist"></Icon>          
              </span>
              <img alt="" class="m-auto tile-product__img" src="https://changiairport.scene7.com/is/image/changiairport/sk-ii-sk-ii-facial-treatment-essence-deluxe-duo-set-mp00051337-1"> 
              <p class="tile-product__promo">  
                  20% Off
              </p>
              <div> 
                  <p class="tile-product__name"> Hugo Boss Femme Women EDP 30ml</p>
                  <div class="tile-product__rating my-xs-10">  
                    <span>* * * * * 120</span> 
                  </div>
                  <p class="tile-product__price"> 
                      <span class="discounted"> AED 2,695.00 </span> 
                      <span class="actual"> AED 2,850.00 </span> 
                  </p>
                  <p class="tile-product__pickup">Immediate Pickup</p>
                  <p class="tile-product__options">4 Options</p>
              </div>
        </div> 
      </swiper-slide>

      <swiper-slide class="d-xs-flex align-item-center swiper-tile-products-carousel">
        <div class="overflow-hidden relative py-xs-30 tile-product"> 
              <span class="tile-product__latest absolute"> SLIDE-5 </span>
              <span class="absolute tile-product__wishlist"> 
                <Icon icon-id="wishlist" class="icon-wishlist"></Icon>          
              </span>
              <img alt="" class="m-auto tile-product__img" src="https://changiairport.scene7.com/is/image/changiairport/sk-ii-sk-ii-facial-treatment-essence-deluxe-duo-set-mp00051337-1"> 
              <p class="tile-product__promo">  
                  20% Off
              </p>
              <div> 
                  <p class="tile-product__name"> Hugo Boss Femme Women EDP 30ml</p>
                  <div class="tile-product__rating my-xs-10">  
                    <span>* * * * * 120</span> 
                  </div>
                  <p class="tile-product__price"> 
                      <span class="discounted"> AED 2,695.00 </span> 
                      <span class="actual"> AED 2,850.00 </span> 
                  </p>
                  <p class="tile-product__pickup">Immediate Pickup</p>
                  <p class="tile-product__options">4 Options</p>
              </div>
        </div> 
      </swiper-slide>

      <swiper-slide class="d-xs-flex align-item-center swiper-tile-products-carousel">
        <div class="overflow-hidden relative py-xs-30 tile-product"> 
              <span class="tile-product__latest absolute"> SLIDE-6 </span>
              <span class="absolute tile-product__wishlist"> 
                <Icon icon-id="wishlist" class="icon-wishlist"></Icon>          
              </span>
              <img alt="" class="m-auto tile-product__img" src="https://changiairport.scene7.com/is/image/changiairport/sk-ii-sk-ii-facial-treatment-essence-deluxe-duo-set-mp00051337-1"> 
              <p class="tile-product__promo">  
                  20% Off
              </p>
              <div> 
                  <p class="tile-product__name"> Hugo Boss Femme Women EDP 30ml</p>
                  <div class="tile-product__rating my-xs-10">  
                    <span>* * * * * 120</span> 
                  </div>
                  <p class="tile-product__price"> 
                      <span class="discounted"> AED 2,695.00 </span> 
                      <span class="actual"> AED 2,850.00 </span> 
                  </p>
                  <p class="tile-product__pickup">Immediate Pickup</p>
                  <p class="tile-product__options">4 Options</p>
              </div>
        </div> 
      </swiper-slide>

      <div class="swiper-scrollbar" slot="scrollbar"></div>
    </swiper>

    <div class="swiper-button-prev" slot="button-prev">
      <Icon icon-id="LeftArrow" class="icon-leftarrow"></Icon> 
    </div>
    <div class="swiper-button-next" slot="button-next">
      <Icon icon-id="RightArrow" class="icon-rightarrow"></Icon>
    </div>
  </div>
</template>



<script>
  import Icon from 'theme/components/custom/Global/Icon'
  import { Swiper, SwiperSlide } from 'vue-awesome-swiper'
  import "swiper/swiper.min.css";

 // core version + navigation, pagination modules:
  import SwiperCore, { Navigation, Pagination, Scrollbar } from 'swiper/core';

  // configure Swiper to use modules
  SwiperCore.use([Navigation, Pagination, Scrollbar]);

  // init Swiper:
  const swiper = new Swiper('.swiper-container', {
     // And if we need scrollbar
    scrollbar: {
      el: '.swiper-scrollbar',
    },
  });

  export default {
    name: 'swiper-scrollbar',
    title: 'Scrollbar',
    components: {
      Icon,
      Swiper,
      SwiperSlide
    },
    data() {
      return {
        swiperOption: {
          slidesPerView: 4,
          spaceBetween: 40,
          slideToClickedSlide: true,
          scrollbar: {
            el: '.swiper-scrollbar',
            draggable: true,
            hide: false,
          },
          navigation: {
            nextEl: '.swiper-button-next',
            prevEl: '.swiper-button-prev'
          }
        }
      }
    }
  }
</script>

<style lang="scss" scoped>

@import '~theme/css/helpers/functions/color';
@import '~theme/css/variables/variables';
@import "swiper/swiper.scss";
  .swiper-products-wrapper {
    @media (min-width: 1024px) {
      position: relative;
      .section-title{
        letter-spacing:1px;
        h5{
          font-size:28px;
          font-weight:400;
        }
        .timer{
          font-size:14px; 
          background:#222; 
          color: white; 
          border-radius:3px;
          font-weight:800;
        }
        .view-all{
          flex-grow:1; 
          font-weight:800;
          letter-spacing:0;
        }
      }
    }
  }
.swiper-tile-products-carousel{
  .tile-product{
    &__latest{
      left:0; 
      top:0; 
      background-color: #e1eef6; 
      color: #0070b2; 
      padding: 3px 10px; 
      border-radius:3px;
      font-size:10px;
      font-weight:800;
      letter-spacing: 2px;
      text-transform: uppercase;
    }
    &__wishlist{
      width:40px;
      height:40px;
      right:0; 
      top:0; 
      .icon-wishlist{
        width: 22px;
        height: 19px;
        fill: color(sdg-clrgray);
      }
    }
    &__img{
      max-width:246px;
    }
    &__promo{
      color: #0070b2; 
      font-size:12px;
      font-weight:800;
      letter-spacing: 2px;
      text-transform: uppercase;
    }
    &__name{
      font-size:14px;
      color:#000;
    }
    &__rating{
      font-size:10px;
      color:#000;
    }
    &__price{
      .discounted{
        font-size:14px;
        color:#222;
        font-weight: 800;
      }
      .actual{
        font-size:10px;
        color:#999;
        text-decoration: line-through;
      }
    }
    &__pickup{
      font-size:14px;
    }
    &__options{
      color:#999;
    }
    p{
      margin:0 0 5px;
    }
  }
}
.swiper-container-horizontal > .swiper-scrollbar{
  width: 80%;
  left: 10% !important;
}
.swiper-button-prev{ 
  left:-50px;
 }
.swiper-button-next{ 
  right:-50px;
}

.swiper-button-next,
.swiper-button-prev {
  height: 40px;
  width: 40px;
  border: solid 1px #ddd;
  border-radius: 20px;
  z-index:1;
  background: #fff;
  --swiper-navigation-color: #222;
  --swiper-navigation-size: 20px;
  

  &:hover {
    border: solid 1px #666;
    --swiper-navigation-color: #000;
  }
  &:after{
    display: none;
  }
}


.icon-leftarrow,
.icon-rightarrow{
    width: 17px;
    height: 14px;
    fill: color(sdg-dark);
  }
</style>

