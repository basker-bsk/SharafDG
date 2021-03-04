<template>
    <div class="slick-master">
      <VueSlickCarousel ref="carousel" v-bind="settings">
            <div class="relative">
              <img src="https://footballqueensland.com.au/wp-content/uploads/2019/01/181231-FQ-New-Brand-NEWS-Web-Banner-1920x480.jpg" alt="">
              <div class="banner-content pl-md-36 pl-lg-80">                  
                    <div class="container">
                      <div class="banner-content-text">
                        <h5>LATEST HEADPHONES</h5>
                        <h2>Your style, your fit.</h2>
                      </div>
                      <div class="banner-content-link">
                        <div class="flex flex-wrap flex-sm-nowrap">
                          <div class="mr-lg-28 mr-sm-12 tab-btn">
                            <ButtonFull color="secondary" class="banner-sec-full">Wireless</ButtonFull>
                          </div>
                          <div class="mr-lg-28 mr-sm-12 tab-btn">
                            <ButtonFull color="secondary" class="banner-sec-full">noise cancellation</ButtonFull>
                          </div>
                          <div class="mr-lg-28 mr-sm-12 tab-btn">
                            <ButtonFull color="secondary" class="banner-sec-full">sports</ButtonFull>
                          </div>
                          <div class="mr-lg-28 mr-sm-12 tab-btn">
                            <ButtonFull color="secondary" class="banner-sec-full">over ears</ButtonFull>
                          </div>
                        </div>
                      </div>
                    </div>
              </div>
            </div>
            <div class="relative">
              <img src="https://nextinteractions.com/wp-content/uploads/2016/08/next-interactions-banner-4.png" alt="">
              <div class="banner-content">                  
                    <div class="container flex justify-md-end">
                      <div class="banner-content-text">
                        <h5>XBOX</h5>
                        <h2>The fastest, most powerful xBox ever.</h2>
                        <ButtonFull color="primary" class="mt-xs-12">SHOP NOW</ButtonFull>
                      </div>
                    </div>
              </div>
            </div>
            <div class="relative">
              <img src="https://footballqueensland.com.au/wp-content/uploads/2019/01/181231-FQ-New-Brand-NEWS-Web-Banner-1920x480.jpg" alt="">
              <div class="banner-content pr-md-80">                  
                    <div class="container flex justify-lg-flex-center">
                      <div class="banner-content-text">
                        <h5>XBOX</h5>
                        <h2>The fastest, most powerful xBox ever.</h2>
                        <ButtonFull color="primary" class="mt-xs-12">SHOP NOW</ButtonFull>
                      </div>
                    </div>
              </div>
            </div>
            <div><img src="https://nextinteractions.com/wp-content/uploads/2016/08/next-interactions-banner-4.png" alt=""></div>
            
            <template #prevArrow>
              <div class="custom-arrow">
                <Icon icon-id="LeftArrow" class="left-icon" />
              </div>
            </template>
          
            <template #nextArrow>
              <div class="custom-arrow">
                <Icon icon-id="RightArrow" class="right-icon" />
              </div>
            </template>
            
            <template #customPaging="page">
              <div class="custom-dot">
                <button><div>{{ page }}</div></button>
              </div>
            </template>
   </VueSlickCarousel>
  </div>
  
</template>

<script>

import VueSlickCarousel from 'vue-slick-carousel'
// import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import Icon from 'theme/components/custom/Global/Icon'
import ButtonFull from 'theme/components/theme/ButtonFull'

export default { 
  name: 'MasterBanner',
  components: {    
    VueSlickCarousel,
    Icon,
    ButtonFull
  },
  data(){
    return {
        settings: {
          arrows: true,
          dots: true,
          fade: true,
          autoplay: true,
          swipeToSlide: false,
          swipe: true,
          touchMove: true,
          draggable: true,
          pauseOnHover: true,
          pauseOnFocus: true,
          pauseOnDotsHover: true,
          autoplaySpeed: 5000,
          infinite: true,
          responsive: [
            {
              breakpoint: 768,
              settings: {                
                fade: true,
              },
            },
          ],
        },
    }
  }
}
</script>

<style  lang="scss">
@import '~theme/css/helpers/functions/color';
@import '~theme/css/variables/variables';

img{
  max-width: 100%;
}
.slick-master {
  width: 100%;
  position: relative;
  .slick-dots li button:before{
    display: none;
  }
  .banner-content{
    position: absolute;
    left: 0;
    right: 0;
    bottom: 20px;
    margin: 0 auto;
    justify-content: center;
    flex-direction: column;
    display: flex;
    z-index: 2;
    @include media(md-up) {
      bottom: 40px;
    }
  }
  .banner-content-text {
    padding-bottom: 2%;
    width: 300px;
    @include media(md-up) {
      padding-bottom: 9%;
      width: 412px;
    }
    h5 {
      font-size: 10px;
      font-weight: bold;
      color: color(white);
      @include media(md-up) {
        font-size: 12px;
      }
    }
    h2 {
      font-size: 28px;
      font-weight: 300;
      color: color(white);
      @include media(md-up) {
        font-size: 42px;
      }
    }
  }

.banner-content-link {  
  display: flex;
  @include media(xs-down) {
    .tab-btn {
      width: 48%; 
      margin-bottom: 10px;   
      button, a {
        padding-left: 10px;
        padding-right: 10px;
      }
      &:nth-child(odd) {
        margin-right: 10px;
      }
    }
  }
}


.banner-sec-full {
   width: 100%;
   white-space: nowrap;
    @include media(lg-up) {
      width: 255px;
    }
}



.slick-prev {
  left: calc(100vw - 1020px);
   @include media(lg-up) {
      left: calc(100vw - 1650px);
    }
}

.slick-next {
    right: calc(100vw - 1020px);
    @include media(lg-up) {
      right: calc(100vw - 1650px);
    }
}

.right-icon, .left-icon {  
  fill: #222;
  width: 13px;
  height: 13px;
  margin: 14px 13px;
    
}
.slick-prev, .slick-next {
  width: 40px;
  height: 40px;
  top: 45%;
  transform: translateY(-45%);
  border: solid 1px color(sdg-dgray);
  background-color: color(white);
  border-radius: 50%;
  z-index: 8;
  position: absolute;  
  cursor: pointer;
}


.slick-dots {
  display: flex !important;
  justify-content: center;
  margin-top: 20px;
}
@media (max-width: 768px) {
    .slick-prev, .slick-next {
      display: none;
    }
}

.slick-slide img {
    display: block;
    margin: 0 auto;
    height: 340px;
   
}

@include media(sm-up) {
    .slick-slide img {
      height: 380px;
    }
 }

 @include media(lg-up) {
    .slick-slide img {
      height: 480px;
    }
 }

.slick-dots li button {
    width: 100%;
    height: .1875rem;
    position: relative;
    display: block;
    overflow: hidden;
    border: none;
}

.slick-dots li button div {
    width: 0;
    height: .1875rem;
    position: absolute;
    left: 0;
    top: 0;
    animation-duration: 6000ms;
    background-color: color(sdg-orange);
    opacity: 1;
    text-indent: -9999px;
}

.slick-dots li {
    display: inline-block;
    width: 39px;
    height: 3px;
    margin-right: 14px;
    position: relative;
    background-color: color(sdg-dgray);    
    cursor: pointer;
}
.slick-dots li.slick-active button div{
  /* -webkit-animation: mymove 5s ease-in-out;  */
  animation-name: mymove;
  animation-timing-function: ease-in-out;
}


.pause-animation {
  -webkit-animation-play-state: paused; /* Safari 4.0 - 8.0 */
  animation-play-state: paused;
}
}
/* Safari 4.0 - 8.0 */
@-webkit-keyframes mymove {
  0% {
    width: 0px;
  }
  85% {
    width: 100%;
  }
  100% {
    width: 125%;
  }
}

@keyframes mymove {
  0% {
    width: 0px;
  }
  85% {
    width: 100%;
  }
  100% {
    width: 125%;
  }
}



  .slick-master:hover  .slick-dots li.slick-active button div {
    -webkit-animation-play-state: paused; /* Safari 4.0 - 8.0 */
    animation-play-state: paused;
  }

</style>
