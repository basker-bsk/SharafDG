<template>
   <div class="image-discover-container container">
      <VueSlickCarousel v-bind="settings">
         <div class="col-sm-12 pb15"
            v-for="(tile, index) in social_tiles"
            :key="index">
            <div>
               <h3>
                  <div class="wrap image-discover-css">
                     <div
                        class="tile middle-xs"
                        >
                        <img
                           class="tile-image"
                           v-lazy="tile.image">
                     </div>
                     <div class="image-discover-parent">
                        <span v-html="tile.heading">{{ tile.heading }}</span>     
                        <p v-html="tile.desc">{{ tile.desc }}</p>
                        <a href="" v-html="tile.link">{{ tile.link }}</a>
                     </div>
                  </div>
               </h3>
            </div>
         </div>
      </VueSlickCarousel>
   </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'
 

export default {
    name: 'MyComponent',
    components: { VueSlickCarousel },
    data() {
      return {
        settings: {
  "centerMode": true,
  "centerPadding": "0px",
  "focusOnSelect": true,
  "infinite": true,
  "slidesToShow": 3,
  "speed": 500,
  "responsive": [
    {
      "breakpoint": 1024,
      "settings": {
        "slidesToShow": 3,
        "slidesToScroll": 3,
        "infinite": false,
        "dots": false,
        "initialSlide": 0
      }
    },
    {
      "breakpoint": 600,
      "settings": {
        "slidesToShow": 2,
        "slidesToScroll": 2,
        "centerPadding": "20px 20px 20px -10px",
        "prevArrow": false,
        "nextArrow": false
      }
    },
    {
      "breakpoint": 480,
      "settings": {
        "slidesToShow": 1,
        "slidesToScroll": 1,
        "centerPadding": "20px 20px 20px -10px",
        "prevArrow": false,
        "nextArrow": false
      }
    }
  ]
},
       social_tiles: [
        {
          image: '/assets/ig/discover1.jpg',
          name: 'Woman practicing on the beach',
          heading: 'Win Prizes!',
          desc: 'Spend more than AED 2,500 to qualify for our lucky draw, T&Cs apply.',
          link: 'Discover Now >'
        },
        {
          image: '/assets/ig/discover2.jpg',
          name: 'Man practicing on the beach',
          heading: 'Fresh start with Sharaf DG grocery',
          desc: 'Fresh goods and essentials delivered right to your home, quality is always assured.',
          link: 'Discover Now >'
        },
        {
          image: '/assets/ig/discover3.jpg',
          name: 'Woman drinks water form the bottle on the beach',
          heading: 'Smartphones bonanza',
          desc: 'Save up to 50% off selected smartphones! While stocks last. T&C apply.',
          link: 'Discover Now >'
        }
      ] 
      }
    }
  }
</script>

<style scoped>
.image-discover-container {
	padding: 0;
}
.image-discover-container .tile {
	display: flex;
	overflow: hidden;
}
.image-discover-container .tile-image {
	width: 100%;
	height: 100%;
	border-top-left-radius: 5px;
	border-top-right-radius: 5px;
}
.image-discover-container .image-discover-parent {
	padding: 10px;
}
.image-discover-container .image-discover-css {
	font-size: 14px !important;
	font-family: 'Roboto', sans-serif;
}
.image-discover-container .image-discover-css span {
	font-weight: bold;
}
.image-discover-container .image-discover-css p {
	font-weight: normal;
}
.image-discover-container .image-discover-css a {
	color: #0072ff!important;
	font-weight: normal;
}

@media only screen and (max-width: 600px) {
	.image-discover-container {
		padding: 0 0 0 20px;
	}
	.image-discover-container .slick-initialized .slick-slide {
		max-width: 270px!important;
	}
  .image-discover-container .col-sm-12.pb15 {
    padding-left: 0;
  }
}
.image-discover-container .v-text-left {
	text-align: left!important;
}
.image-discover-container .wrap {
	background: #f7f7f7!important;
	border-radius: 5px;
	min-height: 435px;
}
.image-discover-container .slick-track {
	margin: 0!important;
}
.image-discover-container .col-sm-12:focus {
	outline: none!important;
}
</style>