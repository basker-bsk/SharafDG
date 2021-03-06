<template>
    <div class="slick-master">
      <VueSlickCarousel ref="carousel" v-bind="settings">
            <div class="relative" 
                  v-for="(item, index) in masterBanner" 
                  :key="index">
                  <show-at :breakpoints="{medium: 993}" breakpoint="mediumAndAbove">
                    <img :src="item.bannerImageDesktop" :alt="item.bannerImageAltText">
                  </show-at>
                  <show-at :breakpoints="{small: 992}" breakpoint="small">
                    <img :src="item.bannerImageMobile" :alt="item.bannerImageAltText">
                  </show-at>
              <div class="banner-content"
                    :class="item.buttons ? 'btnInside' : ''">                  
                    <div class="container"
                     :class="{'pl-md-40 text-align-left' : item.alignment === 'left',
                              'flex justify-md-center text-center' : item.alignment === 'centre',
                              'flex justify-md-flex-end' : item.alignment === 'right'
                            }">
                      <div class="banner-content-text"
                            :class="item.buttons ? 'btnInside' : ''">
                        <h5 :class="{
                              'text-light' : item.textColor === 'light',
                              'text-dark' : item.textColor === 'dark'
                            }">{{ item.bannertitle }}</h5>
                        <h2 :class="{
                              'text-light' : item.textColor === 'light',
                              'text-dark' : item.textColor === 'dark'
                            }">{{ item.bannerShortDesc }}</h2>
                        <div class="mt-xs-10">
                          <ButtonFull :color="item.btnTheme" :link="item.btntextURL" v-if="item.btntext">{{ item.btntext }}</ButtonFull>
                        </div>
                      </div>
                      <div class="banner-content-link" v-if="item.buttons">
                        <div class="flex flex-wrap flex-sm-nowrap">
                          <div class="mr-lg-28 mr-sm-12 tab-btn"
                          v-for="(btns, e) in item.buttons" 
                          :key="e">
                            <ButtonFull :link="btns.btntextURL" :color="btns.btnTheme" class="banner-sec-full">{{btns.btntext}}</ButtonFull>
                          </div>                          
                        </div>
                      </div>
                    </div>
              </div>
            </div>             
            <template #customPaging="page">
              <div class="custom-dot">
                <button><div>{{ page }}</div></button>
              </div>
            </template>
      </VueSlickCarousel>
      <div class="container arrow-container" v-if="masterBanner.length > 1">
        <div class="custom-arrow custom-arrow-left" @click="showPrev">
          <Icon icon-id="LeftArrow" class="left-icon" />
        </div>
        <div class="custom-arrow custom-arrow-right" @click="showNext">
          <Icon icon-id="RightArrow" class="right-icon" />
        </div>
      </div>
  </div>
  
</template>

<script>

import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import Icon from 'theme/components/custom/Global/Icon'
import ButtonFull from 'theme/components/theme/ButtonFull'
import { showAt } from 'vue-breakpoints'

export default {
  name: 'MasterBanner',
  components: {    
    VueSlickCarousel,
    Icon,
    ButtonFull,
    showAt
  },
  data(){
    return {
        masterBanner: [
          {
            "bannerImageDesktop": "https://footballqueensland.com.au/wp-content/uploads/2019/01/181231-FQ-New-Brand-NEWS-Web-Banner-1920x480.jpg",
            "bannerImageMobile": "https://picsum.photos/992/450",
            "bannerImageAltText": "",
            "bannertitle": "latest Headphones",
            "bannerShortDesc": "Your style, your fit.",
            "textColor": "light",
            "btntextURL": "https://via.placeholder.com/750x600.png?text=Banner1",
            "btntext": "",
            "btnTheme": "",
            "alignment": "left",
            "buttons": [
              {
              "btntext": "Wireless12",
              "btntextURL": "https://via.placeholder.com/750x600.png?text=Banner1",
              "btnTheme": "secondary"
              },
              {
              "btntext": "noise cancellation",
              "btntextURL": "https://via.placeholder.com/750x600.png?text=Banner2",
              "btnTheme": "secondary"
              },
              {
              "btntext": "sports",
              "btntextURL": "https://via.placeholder.com/750x600.png?text=Banner3",
              "btnTheme": "secondary"
              },
              {
              "btntext": "over ears",
              "btntextURL": "https://via.placeholder.com/750x600.png?text=Banner4",
              "btnTheme": "secondary"
              }
            ]
          },
            {
            "bannerImageDesktop": "https://nextinteractions.com/wp-content/uploads/2016/08/next-interactions-banner-4.png",
            "bannerImageMobile": "https://nextinteractions.com/wp-content/uploads/2016/08/next-interactions-banner-4.png",
            "bannerImageAltText": "",
            "bannertitle": "latest Headphones centre",
            "bannerShortDesc": "Your style, your fit.",
            "textColor": "light",
            "btntextURL": "https://via.placeholder.com/750x600.png?text=Banner1",
            "btntext": "SHOP NOW",
            "btnTheme": "primary",
            "alignment": "centre",
          },
          {
            "bannerImageDesktop": "https://footballqueensland.com.au/wp-content/uploads/2019/01/181231-FQ-New-Brand-NEWS-Web-Banner-1920x480.jpg",
            "bannerImageMobile": "https://footballqueensland.com.au/wp-content/uploads/2019/01/181231-FQ-New-Brand-NEWS-Web-Banner-1920x480.jpg",
            "bannerImageAltText": "",
            "bannertitle": "latest Headphones right",
            "bannerShortDesc": "Your style, your fit.",
            "textColor": "dark",
            "btntextURL": "https://via.placeholder.com/750x600.png?text=Banner1",
            "btntext": "SHOP NOW",
            "btnTheme": "primary",
            "alignment": "right",
          },
          {
            "bannerImageDesktop": "https://footballqueensland.com.au/wp-content/uploads/2019/01/181231-FQ-New-Brand-NEWS-Web-Banner-1920x480.jpg",
            "bannerImageMobile": "https://footballqueensland.com.au/wp-content/uploads/2019/01/181231-FQ-New-Brand-NEWS-Web-Banner-1920x480.jpg",
            "bannerImageAltText": "",
            "bannertitle": "latest Headphones left",
            "bannerShortDesc": "Your style, your fit.",
            "textColor": "light",
            "btntextURL": "https://via.placeholder.com/750x600.png?text=Banner1",
            "btntext": "SHOP NOW",
            "btnTheme": "secondary",
            "alignment": "left",
          },
           {
            "bannerImageDesktop": "https://nextinteractions.com/wp-content/uploads/2016/08/next-interactions-banner-4.png",
            "bannerImageMobile": "https://nextinteractions.com/wp-content/uploads/2016/08/next-interactions-banner-4.png",
            "bannerImageAltText": "",
            "bannertitle": "",
            "bannerShortDesc": "",
            "textColor": "",
            "btntextURL": "",
            "btntext": "",
            "btnTheme": "",
            "alignment": "",
          },
        
        ],
        settings: {
          arrows: false,
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
          autoplaySpeed: 4600,
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
  },
   methods: {
    showNext() {
      this.$refs.carousel.next();
    },
    showPrev() {
      this.$refs.carousel.prev()
    }
   }
}
</script>

<style lang="scss" scoped>
@import '~theme/css/helpers/functions/color';
@import '~theme/css/variables/variables';

.text-dark {
  color: color(sdg-dark);
}
.text-light {
  color: color(white);
}

.slick-master {
  width: 100%;
  position: relative;
  margin: 0 auto;
  .arrow-container {
    position: absolute;
    left: 0;
    right: 0;
    margin: 0 auto;
    justify-content: center;
    display: flex;
    top: 45%;
    transform: translateY(-45%);
  }
  .banner-content {
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    margin: 0 auto;
    justify-content: center;
    flex-direction: column;
    display: flex;
    z-index: 2;
    &.btnInside {
      bottom: 20px;
      top: auto;
      @include media(md-up) {
        bottom: 40px;
      }
    }
    
    .banner-content-text {
      width: 300px;
       @include media(md-up) {
          width: 412px;
        }
      &.btnInside {
        padding-bottom: 2%;
        @include media(md-up) {
          padding-bottom: 8%;
          width: 412px;
        }        
      }     
      
      h5 {
        font-size: 10px;
        font-weight: bold;
        text-transform: uppercase;
        @include media(md-up) {
          font-size: 12px;
        }
      }
      h2 {
        font-size: 28px;
        font-weight: 300;
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
      .banner-sec-full {
        width: 100%;
        white-space: nowrap;
          @include media(lg-up) {
            width: 255px;
          }
      }
    }
  }

  .right-icon, .left-icon {  
    fill: #222;
    width: 13px;
    height: 13px;
    margin: 14px 13px;      
  }
  .custom-arrow {
    width: 40px;
    height: 40px;
    border: solid 1px color(sdg-dgray);
    background-color: color(white);
    border-radius: 50%;
    z-index: 8;
    position: absolute;  
    cursor: pointer;
    @include media(xs-down) {      
      display: none;
    }
    &.custom-arrow-left {
      left: -20px;
      @include media(lg-up) {
        left: -40px;
      } 
    }
    &.custom-arrow-right {
      right: -20px;
      @include media(lg-up) {
        right: -40px;
      } 
    }    
  }  
  .slick-slide img {
      display: block;
      margin: 0 auto;
      height: 340px;   
      @include media(sm-up) {
        height: 380px;
      } 
       @include media(lg-up) {
          height: 480px;
       }
  }
  
}




.slick-master .slick-dots li.slick-active button div{
  animation-name: mymove;
  animation-timing-function: ease-in-out;
}

.slick-master:hover .slick-dots li.slick-active button div {
    -webkit-animation-play-state: paused; /* Safari 4.0 - 8.0 */
    animation-play-state: paused;
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
</style>