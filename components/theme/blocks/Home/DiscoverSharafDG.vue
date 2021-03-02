<template>
<div class="discover-sharaf ">
    <div class="d-xs-flex flex-column flex-md-row align-item-center container">
        <div class="col-xs-12 col-md-3 pr-xs-0 pl-xs-0 pr-md-20 pr-lg-40 ">
            <h6 class="mt-xs-0 mb-xs-10 text-uppercase font-bold">Discover Sharaf DG</h6>
            <h3 class="m-xs-0 font-normal">Don’t just shop online, discover Sharaf DG</h3>
        </div>
        <div class="d-xs-flex col-xs-12 col-md-9 px-xs-0">
            <VueSlickCarousel v-bind="settings" class="">
            <div class="relative d-xs-flex">
                <div v-for="(item,index) in discoverItems" :key="index" 
                class="items   col-xs-4 px-md-0">
                    <img :src="item.img">
                    <p class="text-center pt-xs-10">{{item.title}}</p>
                </div>
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
                  title:"Discover what’s trending at our blog.",
                  img:"/assets/ig/ig02.jpg"
              },
              {
                  title:"Shop safely in our stores, see our health and hygiene guidelines",
                  img:"/assets/ig/ig03.jpg"
              }

        ],
        settings: {           
            "speed": 500,           
            responsive: [
                {
                    breakpoint: 9999,
                    settings: "unslick"
                },
                {
                    breakpoint: 767,
                    settings: {
                            slidesToShow: 1,
                            slidesToScroll: 1,
                            infinite: true,
                            dots: true
                        }
                }
            ],
        },

      }
    },
}
</script>
<style scoped lang="scss">
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
@import '~theme/css/variables/variables';
.discover-sharaf {
    color: color(sdg-dark);
   
}
@include media(md-up){
.discover-sharaf {
    .items{
        margin: 0 1px;
        &:first-child{
            margin: 0;
            img{
                border-radius: 5px 0 0 5px;
            }
        }
        &:last-child{
            margin: 0;
            img{
                border-radius: 0 5px 5px 0;
            }
        }
    }
}
}

</style>