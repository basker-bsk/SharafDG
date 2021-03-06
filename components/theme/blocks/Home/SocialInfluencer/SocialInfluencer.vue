<template>
<div>
<div class="social-influencer py-xs-25">
    <div class="container pr-xs-0 px-xs-0 px-md-10">
        <div class="row pb-md-20">
            <div class="col-xs-12 col-md-3 flex align-content-center pl-xs-30 pl-md-10">
                <h3 class="fontWeight-300">{{ socialinfluencerList.socialinfluencerTitle }}</h3>
            </div>
            <div class="col-xs-12 col-md-9 pr-xs-0 pr-md-10">
                <div class="card-carousel-wrapper ml-md-80">
                    <div class="card-carousel--nav__left" @click="moveCarousel(-1)" :disabled="atHeadOfList">
                        <Icon icon-id="LeftArrow" class="left-icon" />
                    </div>
                    <div class="card-carousel">
                        <div class="card-carousel--overflow-container">
                            <ul class="card-carousel-cards" :style="{ transform: 'translateX' + '(' + currentOffset + 'px' + ')'}">
                                <li class="card-carousel--card" 
                                    v-for="(item, index) in socialinfluencerList.influencerList" 
                                    :key="index" 
                                    :class="currentTab == index ? 'active' : ''" 
                                    @click="makeActive(index)">
                                    <img :src="item.influencerImageThumbnail" :alt="item.influencerImageAltText"/>
                                </li>
                            </ul>
                        </div>
                    </div>
                    <div class="card-carousel--nav__right" @click="moveCarousel(1)" :disabled="atEndOfList">
                        <Icon icon-id="RightArrow" class="right-icon" />
                    </div>
                </div>
            </div>
        </div>
        <div class="row">
            <div class="col-xs-12">
                <div class="content-tab" v-for="(item, index) in socialinfluencerList.influencerList" :key="index">
                    <div class="content" v-if="currentTab == index" :class="currentTab == index ? 'active' : ''">
                        <div class="row">
                            <div class="col-md-4 order-1 order-md-0">
                               <p class="m0">{{ item.influencerTitle }}</p>
                               <ul class="grid-box d-sm-flex flex-sm-wrap px-xs-12 px-sm-20 py-xs-20 px-md-0 py-md-0">
                                  <li class="flex p-xs-20" v-for="(itemImg, index) in item.productCard" :key="index">
                                     <div class="img-block">
                                       <img :src="itemImg.productImage" :alt="itemImg.productImageAltText" />
                                     </div>
                                     <div class="text-block">
                                       {{ itemImg.productTitle }}
                                     </div>
                                  </li>
                               </ul>
                            </div>
                            <div class="col-md-8 relative px-xs-0 px-md-10" @click="openVideo(item)">
                                <img :src="item.influencerImage" :alt="item.influencerImageAltText" />
                                <div class="align-content-center flex justify-center play-btn"><Icon icon-id="play" class="play-icon" /></div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

<!-- <modal name="modal-video" :width="1200">
    <div class="close" @click.prevent="closeVideo">Close</div>
    <iframe width="1200" height="600" :src="currentVideo.name" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</modal> -->
<VideoPopup  :currentVideoProps="currentVideo" />

</div>
</template>

<script>
import Icon from 'theme/components/custom/Global/Icon'
import Modal from 'theme/components/core/Modal'
import VideoPopup from './VideoPopup'
export default {
  name: 'SocialInfluencer',
    components: {    
        Icon,
        Modal,
        VideoPopup
    },
    data() {
        return {  
          currentVideo: [],
          currentOffset: 0,
          windowSize: 4,
          currentTab: 0,
          currentSlide: 0,
          paginationFactor: 115,
          socialinfluencerList: {
             "socialinfluencerTitle": "#sharafDGPicks",
            influencerList: [
            {
              "influencerImage": "https://picsum.photos/859/350",
              "influencerImageThumbnail": "https://picsum.photos/859/350",
              "influencerImageAltText": "img",
              "influencerTitle": "Mariam Shah's top pick",
              "influencerVideoUrl": "http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4",
              "productCard": [
                  {
                    "productImage": "https://picsum.photos/1060/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Apple Watch Series 6 GPS 44mm Space Grey Aluminum Case with Black Sport Band",
                  },
                  {
                    "productImage": "https://picsum.photos/1061/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Hugo Boss Femme Women EDP 30ml",
                  },
                  {
                    "productImage": "https://picsum.photos/1062/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Armani exchange AX4068S 802913 Havana Women Sunglasses",
                  },
                  {
                    "productImage": "https://picsum.photos/1063/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Daily Cross Bag Lavender",
                  }
              ]
            },
            {
              "influencerImage": "https://picsum.photos/858/350",
              "influencerImageThumbnail": "https://picsum.photos/858/350",
              "influencerImageAltText": "img",
              "influencerTitle": "Mariam Shah's top pick",
              "influencerVideoUrl": "https://www.youtube.com/embed/e-E0UB-YDRk",
              "productCard": [
                  {
                    "productImage": "https://picsum.photos/1064/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Apple Watch Series 6 GPS 44mm Space Grey Aluminum Case with Black Sport Band",
                  },
                  {
                    "productImage": "https://picsum.photos/1065/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Hugo Boss Femme Women EDP 30ml",
                  },
                  {
                    "productImage": "https://picsum.photos/1066/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Armani exchange AX4068S 802913 Havana Women Sunglasses",
                  },
                  {
                    "productImage": "https://picsum.photos/1067/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Daily Cross Bag Lavender",
                  }
              ]
            },
            {
              "influencerImage": "https://picsum.photos/857/350",
              "influencerImageThumbnail": "https://picsum.photos/857/350",
              "influencerImageAltText": "img",
              "influencerTitle": "Mariam Shah's top pick",
              "influencerVideoUrl": "http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4",
              "productCard": [
                  {
                    "productImage": "https://picsum.photos/1060/703",
                    "productImageAltText": "image alt text",
                    "productTitle": "Apple Watch Series 6 GPS 44mm Space Grey Aluminum Case with Black Sport Band",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/704",
                    "productImageAltText": "image alt text",
                    "productTitle": "Hugo Boss Femme Women EDP 30ml",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/705",
                    "productImageAltText": "image alt text",
                    "productTitle": "Armani exchange AX4068S 802913 Havana Women Sunglasses",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/706",
                    "productImageAltText": "image alt text",
                    "productTitle": "Daily Cross Bag Lavender",
                  }
              ]
            },
            {
              "influencerImage": "https://picsum.photos/856/350",
              "influencerImageThumbnail": "https://picsum.photos/856/350",
              "influencerImageAltText": "img",
              "influencerTitle": "Mariam Shah's top pick",
              "influencerVideoUrl": "https://www.youtube.com/embed/e-E0UB-YDRk",
              "productCard": [
                  {
                    "productImage": "https://picsum.photos/1060/707",
                    "productImageAltText": "image alt text",
                    "productTitle": "Apple Watch Series 6 GPS 44mm Space Grey Aluminum Case with Black Sport Band",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/708",
                    "productImageAltText": "image alt text",
                    "productTitle": "Hugo Boss Femme Women EDP 30ml",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/708",
                    "productImageAltText": "image alt text",
                    "productTitle": "Armani exchange AX4068S 802913 Havana Women Sunglasses",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/701",
                    "productImageAltText": "image alt text",
                    "productTitle": "Daily Cross Bag Lavender",
                  }
              ]
            },
            {
              "influencerImage": "https://picsum.photos/855/350",
              "influencerImageThumbnail": "https://picsum.photos/855/350",
              "influencerImageAltText": "img",
              "influencerTitle": "Mariam Shah's top pick",
              "influencerVideoUrl": "http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4",
              "productCard": [
                  {
                    "productImage": "https://picsum.photos/1060/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Apple Watch Series 6 GPS 44mm Space Grey Aluminum Case with Black Sport Band",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Hugo Boss Femme Women EDP 30ml",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Armani exchange AX4068S 802913 Havana Women Sunglasses",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Daily Cross Bag Lavender",
                  }
              ]
            },
            {
              "influencerImage": "https://picsum.photos/854/350",
              "influencerImageThumbnail": "https://picsum.photos/854/350",
              "influencerImageAltText": "img",
              "influencerTitle": "Mariam Shah's top pick",
              "influencerVideoUrl": "http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4",
              "productCard": [
                  {
                    "productImage": "https://picsum.photos/1060/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Apple Watch Series 6 GPS 44mm Space Grey Aluminum Case with Black Sport Band",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Hugo Boss Femme Women EDP 30ml",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Armani exchange AX4068S 802913 Havana Women Sunglasses",
                  },
                  {
                    "productImage": "https://picsum.photos/1060/702",
                    "productImageAltText": "image alt text",
                    "productTitle": "Daily Cross Bag Lavender",
                  }
              ]
            }            
          ]
          },
         
        }
  },

  computed: {
    atEndOfList() {
      return this.currentOffset <= (this.paginationFactor * -1) * (this.socialinfluencerList.influencerList.length - this.windowSize);
    },
    atHeadOfList() {
      return this.currentOffset === 0;
    },
  },
  methods: {
    moveCarousel(direction) {       
      if (direction === 1 && !this.atEndOfList) {
        this.currentOffset -= this.paginationFactor;
      } else if (direction === -1 && !this.atHeadOfList) {
        this.currentOffset += this.paginationFactor;
      }
    },
    makeActive(index) {
      this.currentTab = index;
    },
    openVideo(item) {
        this.$bus.$emit('modal-show', 'modal-video')
        this.currentVideo = item;
    },
    closeVideo() {
      this.$bus.$emit('modal-hide', 'modal-video')      
    }
    
  }
};
</script>

<style lang="scss" scoped>
@import '~theme/css/helpers/functions/color';
@import '~theme/css/variables/variables';
.social-influencer {
  .play-btn {
    cursor: pointer;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
    margin: 0 auto;    
    position: absolute;
    z-index: 2;
    .play-icon {
      fill: color(white);
      width: 50px;
      height: 50px;
    }
  }
    .content-tab {
        .content {
            border-radius: 6px;
            background-color: color(sdg-lightgray);            
            @include media(md-up) {
              height: 257px;
              height: 350px;
            }
            @include media(lg-up) {
              height: 350px;
            }
        }
    } 
    .content-tab {
      position: relative;
      p {
        font-size: 12px;
        font-weight: bold;
        text-transform: uppercase;
        letter-spacing: 2px;
        padding: 15px 0 0 15px;
        @include media(md-up) {
          padding: 30px 0 0 30px;
        }
      }
      .grid-box {        
        @include media(md-up) {
          width: 530px;
          position: absolute;
          top: 55px;
          left: 25px;        
          z-index: 3;
        }
        @include media(lg-up) {
          width: 700px;
        }
        li {
          background-color: color(white);
          border-radius: 6px;
          margin-bottom: 10px;
          padding: 20px 30px 20px 10px;          
          @include media(sm-up) {
              width: 48%;
              margin: 5px;
            }
          @include media(md-up) {
              width: 257px;
            }
            @include media(lg-up) {
              width: 310px;
            }
          &:nth-child(odd) {
            @include media(sm-up) {
              margin-left: 0;
            }
          }
          .img-block {
            margin-right: 10px;
            width: 30%;
            img {
              width: 100%;
              height: 83px;
            }
          }
          .text-block {
            width: 70%;
            color: color(sdg-dark);
          }
        }
      }
    }
}

.card-carousel-wrapper .right-icon, .card-carousel-wrapper .left-icon {  
  fill: color(sdg-dark);
  width: 13px;
  height: 13px;    
}

.card-carousel-wrapper {
  display: flex;
  align-items: center;
  @include media(md-down) {
      overflow-x: auto;
  }
}

.card-carousel {
  display: flex;
  justify-content: center;
  @include media(md-up) {
      width: 470px;
  }
}

.card-carousel--overflow-container {
  overflow-x: auto;
  @include media(md-up) {
      overflow: hidden;
  }
}

.card-carousel--nav__left, .card-carousel--nav__right {
  display: inline-block;
  cursor: pointer;
  margin: 0 20px;
    @include media(md-down) {
        display: none;
    }
}
.card-carousel--nav__left[disabled], .card-carousel--nav__right[disabled] {
  opacity: 0.2;
}

.card-carousel-cards {
  display: flex;
  padding: 20px;
  @include media(md-up) {
     padding: 0;
     width: 100vw;
     transition: transform 150ms ease-out;   
     transform: translatex(0px); 
  }
}
.card-carousel-cards .card-carousel--card {
  margin: 0 5px; 
  cursor: pointer;
  width: 98px;
  height: 98px;
  background-color: color(white);
  border-radius: 9999px;
  padding: 7px;
  z-index: 3;
  border: 2px solid color(white);
  @include media(md-up) { 
       margin: 0 10px;     
       height: 99px;
       width: 99px;
       padding: 8px;
  }
}
.card-carousel-cards .card-carousel--card.active{ 
    border-color: color(sdg-orange);
}
.card-carousel-cards .card-carousel--card:first-child {
  margin-left: 0;
}
.card-carousel-cards .card-carousel--card:last-child {
  margin-right: 0;
}
.card-carousel-cards .card-carousel--card img {
  vertical-align: bottom;
  border-radius: 9999px;
  transition: opacity 150ms linear;
  user-select: none;
  width: 100%;
  height: 100%;
}
.card-carousel-cards .card-carousel--card img:hover {
  opacity: 0.8;
}

</style>