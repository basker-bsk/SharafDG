<template>
<div class="discover-sharaf">
    <div class="d-xs-flex flex-column flex-md-row align-item-center container pr-xs-0">
        <div class="col-xs-12 col-md-3 pr-xs-0 pl-xs-0 pr-md-20 pr-lg-40 mb-xs-30 mb-md-0">
            <h6 class="mt-xs-0 mb-xs-10 text-uppercase font-bold">Discover Sharaf DG</h6>
            <h3 class="m-xs-0 font-normal">Don't just shop online, discover Sharaf DG</h3>
        </div>
        <div class="d-xs-flex d-md-block col-xs-12 col-md-9 px-xs-0">
            <VueSlickCarousel v-bind="settings" class="">
                <div v-for="(item,index) in discoverItems" :key="index"
                class="items px-md-0 pr-xs-10">
                    <img :src="item.img">
                    <p class="text-center pt-xs-10">{{item.title}}</p>
                </div>
            </VueSlickCarousel>
    </div>
    </div>
</div>
</template>
<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
export default {
    name:'DiscoverSharafDG',
    components: {
        VueSlickCarousel,
    },
    data() {
      return {
        discoverItems:[
              {
                  title:"Be a Sharaf DG Member and be rewarded!",
                  img:"/assets/ig/ig01.jpg"
              },
              {
                  title:"Discover what's trending at our blog.",
                  img:"/assets/ig/ig02.jpg"
              },
              {
                  title:"Shop safely in our stores, see our health and hygiene guidelines",
                  img:"/assets/ig/ig03.jpg"
              }
        ],
        settings: {
                "dots": false,
                "arrows": false,
                "infinite": false,
                "slidesToShow": 3,
                "slidesToScroll": 3,
                "responsive": [
                    {
                    "breakpoint": 1300,
                    "settings": {
                        "slidesToShow": 3,
                        "slidesToScroll": 3,
                    }
                    },
                    {
                    "breakpoint": 600,
                    "settings": {
                        "slidesToShow": 2.2,
                        "slidesToScroll": 1,
                    }
                    },
                    {
                    "breakpoint": 480,
                    "settings": {
                        "slidesToShow": 1.2,
                        "slidesToScroll": 1
                    }
                    }
                ]
                },
      }
    },
}
</script>
<style lang="scss">
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
@import '~theme/css/variables/variables';

.discover-sharaf {
    color: color(sdg-dark);
   .slick-list  {    
       @include media(md-down) {
        overflow: visible;
       }    
    }
    * {
    min-width: 0;
    min-height: 0;
    }
}
@include media(md-down){
.discover-sharaf {
    .slick-slide{
        img{
            border-radius: 5px;
        }
    }
}
}
@include media(md-up){
.discover-sharaf {
     .slick-slide{
        border-left: 1px solid color(white);
        &:first-child{
            img{
                border-radius: 10px 0 0 10px;
            }
        }
        &:last-child{
            img{
                border-radius: 0 10px 10px 0;
            }
        }
    }
}
}
</style>