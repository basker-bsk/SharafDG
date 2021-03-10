<template>
  <div class="header">
    <header class="z-xs-10 w-100 header header--banner ">
      <div class="header__main header-container py-xs-10 align-item-center d-xs-flex py-md-0 bg-cl-sdg-blue ">
        <div class="container">
        <div class="align-item-center d-xs-flex"  v-if="!isCheckoutPage || isThankYouPage">       
            <div class="middle-xs d-xs-flex d-md-none">
                <MobileMenuContainer :menuitems="menu" />                
            </div>
            <div class="header__logo-wrapper d-xs-flex middle-xs">
                <logo  alt="" width="auto" height="auto" />
            </div>
           <Search />
            <div class="header__right-wrapper justify-md-space-between ml-lg-20 d-xs-flex align-item-center">
                <lang-icon class="icon cl-white d-xs-none d-md-flex pointer" />
                <account-icon class="icon  d-xs-none d-md-flex pointer" />
                <microcart-icon class="icon pointer middle-xs" />
            </div>          
          <div class="row between-xs middle-xs px15 py5 " v-if="isCheckoutPage && !isThankYouPage">
            <div class="col-xs-5 col-md-3 middle-xs">
              <div>
                <router-link
                  :to="localizedRoute('/')"
                  class="cl-tertiary links"
                >
                  {{ $t('Return to shopping') }}
                </router-link>
              </div>
            </div>
            <div class="col-xs-2 col-md-6 center-xs">
              <logo width="auto" height="41px" />
            </div>
            <div class="col-xs-5 col-md-3 end-xs">
              <div>
                <a
                  v-if="!currentUser"
                  href="#"
                  @click.prevent="gotoAccount"
                  class="cl-tertiary links"
                >{{ $t('Login to your account') }}</a>
                <span v-else>{{ $t('You are logged in as {firstname}', currentUser) }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
      </div>
      
    </header>
    <DesktopMenu class="d-none d-xs-flex" :categoryitems="menu" />
  </div>
</template>

<script>
import { mapState } from 'vuex'
import CurrentPage from 'theme/mixins/currentPage'
import Logo from 'theme/components/core/Logo'
import MicrocartIcon from 'theme/components/core/blocks/Header/MicrocartIcon'
import DesktopMenu from './Desktop/DesktopMenu'
import AccountIcon from './Desktop/AccountIcon'
import MobileMenuContainer from './Mobile/index'
import Search from './Shared/Search'
import LangIcon from './Shared/LangIcon'

export default {
  name: 'Header',
  components: {
    AccountIcon,
    Logo,
    MicrocartIcon,
    DesktopMenu,
    MobileMenuContainer,
    LangIcon,
    Search,
  },
  mixins: [CurrentPage],
  data () {
    return {
      navVisible: true,
      scrolling: false,
      scrollTop: 0,
      lastScrollTop: 0,
      navbarHeight: 54,
      isHovering: false,      
      isFixedHeader: false,      
      menu: {
      "categories": {
        "category": {
          "categoryItems": [      
            {
              "httpStatusCode": 0,
              "url": "/en/category/beauty",
              "id": "beauty",
              "name": "Beauty",
              "brands": [
                {
                  "url": "/en/brand/chanel",
                  "openNewTab": "",
                  "id": "chanel",
                  "name": "CHANEL"
                },
                {
                  "url": "/en/brand/cosme-decorte",
                  "openNewTab": "",
                  "id": "cosme-decorte",
                  "name": "COSME DECORTE"
                },
                {
                  "url": "/en/brand/clarins",
                  "openNewTab": "",
                  "id": "clarins",
                  "name": "CLARINS"
                },
                {
                  "url": "/en/brand/estee-lauder",
                  "openNewTab": "",
                  "id": "estee-lauder",
                  "name": "ESTÉE LAUDER"
                },
                {
                  "url": "/en/brand/kiehls",
                  "openNewTab": "",
                  "id": "kiehls",
                  "name": "KIEHL'S"
                },
                {
                  "url": "/en/brand/lancome",
                  "openNewTab": "",
                  "id": "lancome",
                  "name": "Lancome"
                },
                {
                  "url": "/en/brand/la-mer",
                  "openNewTab": "",
                  "id": "la-mer",
                  "name": "LA MER"
                },
                {
                  "url": "/en/brand/sulwhasoo",
                  "openNewTab": "",
                  "id": "sulwhasoo",
                  "name": "SULWHASOO"
                },
                {
                  "url": "/en/brand/sk-ii",
                  "openNewTab": "",
                  "id": "sk-ii",
                  "name": "Sk-II"
                },
                {
                  "url": "/en/brand/yves-saint-laurent",
                  "openNewTab": "",
                  "id": "yves-saint-laurent",
                  "name": "YVES SAINT LAURENT"
                }
              ],
              "subcategories": [
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/beauty",
                  "id": "beauty-see-all",
                  "name": "See All"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/beauty?newArrival=true",
                  "id": "beauty|newArrival",
                  "name": "New Arrivals"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/beauty?giftAndValueSet=true",
                  "id": "beauty|giftAndValueSet",
                  "name": "Gifts & Values Sets"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/beauty?travelExclusive=true",
                  "id": "beauty|travelExclusive",
                  "name": "Travel Exclusives"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/beauty?promo=true",
                  "id": "beauty|promo",
                  "name": "Sale"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/beauty/make-up",
                  "id": "make-up",
                  "name": "MakeUp",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/make-up/face",
                      "id": "face",
                      "name": "Face"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/make-up/eye",
                      "id": "eye",
                      "name": "Eye"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/make-up/cheek-make-up",
                      "id": "cheek-make-up",
                      "name": "Cheek"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/make-up/make-up-accessories",
                      "id": "make-up-accessories",
                      "name": "Accessories"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/make-up/make-up-gadgets",
                      "id": "make-up-gadgets",
                      "name": "Beauty Gadgets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/make-up/make-up-gifts-and-value-sets",
                      "id": "make-up-gifts-and-value-sets",
                      "name": "Gifts & Value Sets"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/beauty/skincare",
                  "id": "skincare",
                  "name": "Skin Care",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/skincare/skincare-cleanser-and-exfliotation",
                      "id": "skincare-cleanser-and-exfliotation",
                      "name": "Cleanser & Exfliotation"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/skincare/skincare-moisturisers-and-mists",
                      "id": "skincare-moisturisers-and-mists",
                      "name": "Moisturisers & Mists"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/skincare/skincare-eye-care",
                      "id": "skincare-eye-care",
                      "name": "Eye Care"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/skincare/skincare-lotion-serum-essence",
                      "id": "skincare-lotion-serum-essence",
                      "name": "Lotion, Serum & Essence"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/skincare/skincare-mask",
                      "id": "skincare-mask",
                      "name": "Mask"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/skincare/skincare-sun-care",
                      "id": "skincare-sun-care",
                      "name": "Sun Care"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/skincare/skincare-accessories",
                      "id": "skincare-accessories",
                      "name": "Accessories"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/skincare/skincare-gifts-and-value-sets",
                      "id": "skincare-gifts-and-value-sets",
                      "name": "Gifts & Value Sets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/skincare/skincare-cleanser-and-exfoliation",
                      "id": "skincare-cleanser-and-exfoliation",
                      "name": "Cleanser & Exfoliation"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/skincare/skincare-lip-treatment",
                      "id": "skincare-lip-treatment",
                      "name": "Lip Treatment"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/beauty/fragrances",
                  "id": "fragrances",
                  "name": "Fragrance",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/fragrances/women-fragrances",
                      "id": "women-fragrances",
                      "name": "Women"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/fragrances/men-fragrances",
                      "id": "men-fragrances",
                      "name": "Men"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/fragrances/unisex-fragrances",
                      "id": "unisex-fragrances",
                      "name": "Unisex"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/fragrances/fragrances-gifts-and-value-sets",
                      "id": "fragrances-gifts-and-value-sets",
                      "name": "Gifts & Value Sets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/fragrances/signature-fragrances",
                      "id": "signature-fragrances",
                      "name": "SIGNATURE FRAGRANCES"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/fragrances/private-blend-fragrances",
                      "id": "private-blend-fragrances",
                      "name": "PRIVATE BLEND FRAGRANCES"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/beauty/haircare",
                  "id": "haircare",
                  "name": "Hair Care",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/haircare/haircare-shampoos-and-conditioners",
                      "id": "haircare-shampoos-and-conditioners",
                      "name": "Shampoos & Conditioners"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/haircare/haircare-treatements",
                      "id": "haircare-treatements",
                      "name": "Treatments"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/haircare/haircare-styling-products",
                      "id": "haircare-styling-products",
                      "name": "Styling Produc"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/haircare/haircare-hair-tools",
                      "id": "haircare-hair-tools",
                      "name": "Hair Tools"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/haircare/haircare-accessories",
                      "id": "haircare-accessories",
                      "name": "Accessories"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/haircare/haircare-gifts-and-value-sets",
                      "id": "haircare-gifts-and-value-sets",
                      "name": "Gifts & Value Sets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/haircare/hairCare-shampoo-and-conditioner",
                      "id": "hairCare-shampoo-and-conditioner",
                      "name": "Shampoos & Conditioners"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/haircare/hairCare-treatments",
                      "id": "hairCare-treatments",
                      "name": "Treatments"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/beauty/bath-and-body",
                  "id": "bath-and-body",
                  "name": "Bath & Body",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/bath-and-body-bodywash-and-shower",
                      "id": "bath-and-body-bodywash-and-shower",
                      "name": "Body Wash & Shower"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/bath-and-body-gels-scrubs-exfliotators",
                      "id": "bath-and-body-gels-scrubs-exfliotators",
                      "name": "Gels, Scrubs & Exfoliators"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/bath-and-body-bathoils",
                      "id": "bath-and-body-bathoils",
                      "name": "Bath Oils"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/bath-and-body-soaps",
                      "id": "bath-and-body-soaps",
                      "name": "Soaps"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/bath-and-body-moisturisers",
                      "id": "bath-and-body-moisturisers",
                      "name": "Moisturisers"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/bath-and-body-treatments",
                      "id": "bath-and-body-treatments",
                      "name": "Treatments"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/bath-and-body-hand-and-foot-care",
                      "id": "bath-and-body-hand-and-foot-care",
                      "name": "Hand & Foot Care"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/bath-and-body-gifts-and-value-sets",
                      "id": "bath-and-body-gifts-and-value-sets",
                      "name": "Gifts & Value Sets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/bath-and-body-gels-scrubs-exfoliators",
                      "id": "bath-and-body-gels-scrubs-exfoliators",
                      "name": "Gels, Scrubs & Exfoliators"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/body-hand-wash",
                      "id": "body-hand-wash",
                      "name": "BODY & HAND WASH"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/body-hand-lotion",
                      "id": "body-hand-lotion",
                      "name": "BODY & HAND LOTION"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/bath-soaps",
                      "id": "bath-soaps",
                      "name": "BATH SOAPS"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/body-cremes",
                      "id": "body-cremes",
                      "name": "BODY CRÈMES"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/shower-gels",
                      "id": "shower-gels",
                      "name": "SHOWER GELS"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/vitamin-e",
                      "id": "vitamin-e",
                      "name": "VITAMIN E"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/body-scrubs",
                      "id": "body-scrubs",
                      "name": "BODY SCRUBS"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/hand-cream",
                      "id": "hand-cream",
                      "name": "HAND CREAM"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/hair-mist",
                      "id": "hair-mist",
                      "name": "HAIR MIST"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/lip-care",
                      "id": "lip-care",
                      "name": "LIP CARE"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/bath-and-body/little-luxuries",
                      "id": "little-luxuries",
                      "name": "LITTLE LUXURIES"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/beauty/luxe-beauty",
                  "id": "luxe-beauty",
                  "name": "Luxe Beauty",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/luxe-beauty/luxe-beauty-make-up",
                      "id": "luxe-beauty-make-up",
                      "name": "MakeUp"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/beauty/luxe-beauty/luxe-beauty-skincare",
                      "id": "luxe-beauty-skincare",
                      "name": "Skincare"
                    }
                  ]
                }
              ]
            },
            {
              "httpStatusCode": 0,
              "url": "/en/category/electronics",
              "id": "electronics",
              "name": "Electronics",
              "brands": [
                {
                  "url": "/en/brand/apple",
                  "openNewTab": "",
                  "id": "apple",
                  "name": "APPLE"
                },
                {
                  "url": "/en/brand/bose",
                  "openNewTab": "",
                  "id": "bose",
                  "name": "BOSE"
                },
                {
                  "url": "/en/brand/fitbit",
                  "openNewTab": "",
                  "id": "fitbit",
                  "name": "FITBIT"
                },
                {
                  "url": "/en/brand/garmin",
                  "openNewTab": "",
                  "id": "garmin",
                  "name": "GARMIN"
                },
                {
                  "url": "/en/brand/gopro",
                  "openNewTab": "",
                  "id": "gopro",
                  "name": "GOPRO"
                },
                {
                  "url": "/en/brand/huawei",
                  "openNewTab": "",
                  "id": "huawei",
                  "name": "HUAWEI"
                },
                {
                  "url": "/en/brand/nakamichi",
                  "openNewTab": "",
                  "id": "nakamichi",
                  "name": "NAKAMICHI"
                },
                {
                  "url": "/en/brand/panasonic",
                  "openNewTab": "",
                  "id": "panasonic",
                  "name": "PANASONIC"
                },
                {
                  "url": "/en/brand/philips",
                  "openNewTab": "",
                  "id": "philips",
                  "name": "PHILIPS"
                },
                {
                  "url": "/en/brand/sony",
                  "openNewTab": "",
                  "id": "sony",
                  "name": "SONY"
                }
              ],
              "subcategories": [
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics",
                  "id": "electronics-see-all",
                  "name": "See All"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics?newArrival=true",
                  "id": "electronics|newArrival",
                  "name": "New Arrivals"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics",
                  "id": "electronics-best-sellers",
                  "name": "Best Sellers"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics?promo=true",
                  "id": "electronics|promo",
                  "name": "Sale"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics/audio",
                  "id": "audio",
                  "name": "Audio",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/audio/audio-earphones",
                      "id": "audio-earphones",
                      "name": "Earphones"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/audio/audio-wired-headphones",
                      "id": "audio-wired-headphones",
                      "name": "Wired Headphones"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/audio/audio-wireless-headphones",
                      "id": "audio-wireless-headphones",
                      "name": "Wireless Headphones"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/audio/audio-speakers",
                      "id": "audio-speakers",
                      "name": "Speakers"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/audio/audio-mp3-players",
                      "id": "audio-mp3-players",
                      "name": "MP3 Players"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics/laptop-and-pc",
                  "id": "laptop-and-pc",
                  "name": "Laptops & PC",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/laptop-and-pc/laptop-and-pc-notebooks",
                      "id": "laptop-and-pc-notebooks",
                      "name": "Notebooks"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/laptop-and-pc/laptop-and-pc-computers",
                      "id": "laptop-and-pc-computers",
                      "name": "Computers"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/laptop-and-pc/laptop-and-pc-presenters",
                      "id": "laptop-and-pc-presenters",
                      "name": "Presenters"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/laptop-and-pc/laptop-and-pc-voice-recorders",
                      "id": "laptop-and-pc-voice-recorders",
                      "name": "Voice Recorders"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/laptop-and-pc/laptop-and-pc-mouse-and-keyboards",
                      "id": "laptop-and-pc-mouse-and-keyboards",
                      "name": "Mouse & Keyboards"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/laptop-and-pc/laptop-and-pc-accessories",
                      "id": "laptop-and-pc-accessories",
                      "name": "Accessories"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/laptop-and-pc/laptop-and-pc-smart-tv-players",
                      "id": "laptop-and-pc-smart-tv-players",
                      "name": "Smart TV Players"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics/camera-and-video",
                  "id": "camera-and-video",
                  "name": "Camera & Video",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/camera-and-video/camera-and-video-compact-digital-camera",
                      "id": "camera-and-video-compact-digital-camera",
                      "name": "Compact Digital Camera"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/camera-and-video/camera-and-video-interchangeable-lens-camera",
                      "id": "camera-and-video-interchangeable-lens-camera",
                      "name": "Interchangeable Lens Camera"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/camera-and-video/camera-and-video-binoculars",
                      "id": "camera-and-video-binoculars",
                      "name": "Binoculars"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/camera-and-video/camera-and-video-instant-camera",
                      "id": "camera-and-video-instant-camera",
                      "name": "Instant Camera"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/camera-and-video/camera-and-video-action-camera",
                      "id": "camera-and-video-action-camera",
                      "name": "Action Camera"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/camera-and-video/camera-and-video-drones",
                      "id": "camera-and-video-drones",
                      "name": "Drones"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/camera-and-video/camera-and-video-video-camera-and-camcorder",
                      "id": "camera-and-video-video-camera-and-camcorder",
                      "name": "Video Camera & Camcorder"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics/mobile-and-smart-devices",
                  "id": "mobile-and-smart-devices",
                  "name": "Mobile & Smart Devices",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/mobile-and-smart-devices/mobile-and-smart-devices-mobile-phones",
                      "id": "mobile-and-smart-devices-mobile-phones",
                      "name": "Mobile phones"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/mobile-and-smart-devices/mobile-and-smart-devices-tablets",
                      "id": "mobile-and-smart-devices-tablets",
                      "name": "Tablets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/mobile-and-smart-devices/mobile-and-smart-devices-wearables",
                      "id": "mobile-and-smart-devices-wearables",
                      "name": "Wearables"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/mobile-and-smart-devices/mobile-and-smart-devices-accessories-and-cases",
                      "id": "mobile-and-smart-devices-accessories-and-cases",
                      "name": "Accessories & Cases"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics/electronics-personal-care",
                  "id": "electronics-personal-care",
                  "name": "Personal Care",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/electronics-personal-care/electronics-personal-care-beauty-devices",
                      "id": "electronics-personal-care-beauty-devices",
                      "name": "Beauty Devices"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/electronics-personal-care/electronics-personal-care-oral-care",
                      "id": "electronics-personal-care-oral-care",
                      "name": "Oral Care"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/electronics-personal-care/electronics-personal-care-grooming-devices",
                      "id": "electronics-personal-care-grooming-devices",
                      "name": "Grooming Devices"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/electronics-personal-care/electronics-personal-care-hair-tools",
                      "id": "electronics-personal-care-hair-tools",
                      "name": "Hair Tools"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics/gaming-and-toys",
                  "id": "gaming-and-toys",
                  "name": "Gaming & Toys",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/gaming-and-toys/gaming-and-toys-gaming-game-accessories",
                      "id": "gaming-and-toys-gaming-game-accessories",
                      "name": "Game Accessories"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/gaming-and-toys/gaming-and-toys-gaming-consoles",
                      "id": "gaming-and-toys-gaming-consoles",
                      "name": "Gaming Consoles"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/gaming-and-toys/gaming-and-toys-gaming-experimental-toys",
                      "id": "gaming-and-toys-gaming-experimental-toys",
                      "name": "Experimental Toys"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics/household",
                  "id": "household",
                  "name": "Household",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/household/household-home-electronics",
                      "id": "household-home-electronics",
                      "name": "Home Electronics"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/household/household-kitchen-accessories",
                      "id": "household-kitchen-accessories",
                      "name": "Kitchen Accessories"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/household/household-kitchen-electronics",
                      "id": "household-kitchen-electronics",
                      "name": "Kitchen Electronics"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/electronics/health-care",
                  "id": "health-care",
                  "name": "Health Care",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/electronics/health-care/health-care-health-gadgets",
                      "id": "health-care-health-gadgets",
                      "name": "Health Gadgets"
                    }
                  ]
                }
              ]
            },
            {
              "httpStatusCode": 0,
              "url": "/en/category/services",
              "id": "services",
              "name": "Services",
              "subcategories": [
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/services/connectivity",
                  "id": "connectivity",
                  "name": "Connectivity",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/services/connectivity/prepaid-sim-cards",
                      "id": "prepaid-sim-cards",
                      "name": "Prepaid Sim Cards"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/services/connectivity/portable-wifi-routers",
                      "id": "portable-wifi-routers",
                      "name": "Portable Wifi Routers"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/services/attractions-and-entertainment",
                  "id": "attractions-and-entertainment",
                  "name": "Attractions & Entertainment",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/services/attractions-and-entertainment/attraction-tickets",
                      "id": "attraction-tickets",
                      "name": "Attraction Tickets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/services/attractions-and-entertainment/entertaintment-and-activities",
                      "id": "entertaintment-and-activities",
                      "name": "Entertaintment & Activities"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/services/attractions-and-entertainment/day-tours",
                      "id": "day-tours",
                      "name": "Day Tours"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/services/attractions-and-entertainment/entertainment-and-activities",
                      "id": "entertainment-and-activities",
                      "name": "Entertainment & Activities"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/services/reservations",
                  "id": "reservations",
                  "name": "Reservations"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/services/forex-and-insurance",
                  "id": "forex-and-insurance",
                  "name": "Forex & Insurance"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/services/flight-addons",
                  "id": "flight-addons",
                  "name": "Flight Add-Ons"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/services/attractions-and-entertainment%20test",
                  "id": "attractions-and-entertainment test",
                  "name": "Attractions & Entertainment test",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/services/attractions-and-entertainment%20test/attraction-tickets",
                      "id": "attraction-tickets",
                      "name": "Attraction Tickets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/services/attractions-and-entertainment%20test/entertainment-and-activities",
                      "id": "entertainment-and-activities",
                      "name": "Entertainment & Activities"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/services/attractions-and-entertainment%20test/day-tours",
                      "id": "day-tours",
                      "name": "Day Tours"
                    }
                  ]
                }
              ]
            },
 
          ],
          "link": {
            "emptyMenu": false,
            "title": "Shop All Products12"
          },
          ":type": "ishop/components/content/category"
        }
      },
      "services": {
        "services": {
          "bannerTitle": "SPECTACULAR SIGHTS",
          "promotedTitle": "24/7 CONNECTIVITY",
          "promotedIcon": "/content/dam/cagishop/home/header/services/connectivity/connectivity_gradient.svg",
          "bannerIcon": "/content/dam/cagishop/home/header/services/attractions/attractions_gradient.svg",
          "categories": [
            {
              "httpStatusCode": 0,
              "url": "/connectivity",
              "id": "connectivity",
              "name": "Connectivity",
              "subcategories": [
                {
                  "httpStatusCode": 0,
                  "url": "/prepaid-sim-cards",
                  "id": "prepaid-sim-cards",
                  "name": "Prepaid Sim Cards"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/portable-wifi-routers",
                  "id": "portable-wifi-routers",
                  "name": "Portable Wifi Routers"
                }
              ]
            },
            {
              "httpStatusCode": 0,
              "url": "/attractions-and-entertainment",
              "id": "attractions-and-entertainment",
              "name": "Attractions & Entertainment",
              "subcategories": [
                {
                  "httpStatusCode": 0,
                  "url": "/attraction-tickets",
                  "id": "attraction-tickets",
                  "name": "Attraction Tickets"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/entertaintment-and-activities",
                  "id": "entertaintment-and-activities",
                  "name": "Entertaintment & Activities"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/day-tours",
                  "id": "day-tours",
                  "name": "Day Tours"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/entertainment-and-activities",
                  "id": "entertainment-and-activities",
                  "name": "Entertainment & Activities"
                }
              ]
            },
            {
              "httpStatusCode": 0,
              "url": "/reservations",
              "id": "reservations",
              "name": "Reservations"
            },
            {
              "httpStatusCode": 0,
              "url": "/forex-and-insurance",
              "id": "forex-and-insurance",
              "name": "Forex & Insurance"
            },
            {
              "httpStatusCode": 0,
              "url": "/flight-addons",
              "id": "flight-addons",
              "name": "Flight Add-Ons"
            },
            {
              "httpStatusCode": 0,
              "url": "/attractions-and-entertainment%20test",
              "id": "attractions-and-entertainment test",
              "name": "Attractions & Entertainment test",
              "subcategories": [
                {
                  "httpStatusCode": 0,
                  "url": "/attraction-tickets",
                  "id": "attraction-tickets",
                  "name": "Attraction Tickets"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/entertainment-and-activities",
                  "id": "entertainment-and-activities",
                  "name": "Entertainment & Activities"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/day-tours",
                  "id": "day-tours",
                  "name": "Day Tours"
                }
              ]
            }
          ],
          "link": {
            "emptyMenu": false,
            "title": "Services"
          },
          ":type": "ishop/components/home/services"
        }
      },
      "brands": {
        "brand": {
          "sectionType": "header",
          "exclusiveBrandsTitle": "Featured Brands",
          "atoz": "All Brands A-Z",
          "searchPlaceholder": "Search brands",
          "viewAll": "See All Brands",
          "viewAllRedirectUrl": "/en/brand-dictionary",
          "exclusiveBrandDetails": [
            {
              "redirectUrl": "/en/brand/apple",
              "name": "Apple",
              "code": "apple",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://dummyimage.com/70x50/aaa/222&text=image1"
            },
            {
              "redirectUrl": "/en/brand/chanel",
              "name": "Samsung",
              "code": "samsung",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://dummyimage.com/70x50/aaa/222&text=image2"
            },
            {
              "redirectUrl": "/en/brand/apple",
              "name": "Apple",
              "code": "apple",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://dummyimage.com/70x50/aaa/222&text=image3"
            },
             {
              "redirectUrl": "/en/brand/apple",
              "name": "Apple",
              "code": "apple",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://dummyimage.com/70x50/aaa/222&text=image4"
            },
             {
              "redirectUrl": "/en/brand/apple",
              "name": "Apple",
              "code": "apple",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://dummyimage.com/70x50/aaa/222&text=image1"
            },
            {
              "redirectUrl": "/en/brand/chanel",
              "name": "Samsung",
              "code": "samsung",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://dummyimage.com/70x50/aaa/222&text=image2"
            },
            {
              "redirectUrl": "/en/brand/apple",
              "name": "Apple",
              "code": "apple",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://dummyimage.com/70x50/aaa/222&text=image3"
            },
             {
              "redirectUrl": "/en/brand/apple",
              "name": "Apple",
              "code": "apple",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://dummyimage.com/70x50/aaa/222&text=image4"
            },
          
          ],
          "brandList": [
            {
              "brands": [
                {
                  "url": "/en/home",
                  "openNewTab": "",
                  "id": "128-durian",
                  "name": "128 Durian"
                },
                {
                  "url": "/en/brand/1513",
                  "openNewTab": "true",
                  "id": "1513",
                  "name": "1513"
                },
                {
                  "url": "/en/brand/155-south-bridge",
                  "openNewTab": "",
                  "id": "155-south-bridge",
                  "name": "155 SOUTH BRIDGE"
                },
                {
                  "url": "/en/brand/1751",
                  "openNewTab": "",
                  "id": "1751",
                  "name": "1751"
                },
                {
                  "url": "/en/brand/1800-tequila",
                  "openNewTab": "",
                  "id": "1800-tequila",
                  "name": "1800 TEQUILA"
                },
                {
                  "url": "/en/brand/1914",
                  "openNewTab": "",
                  "id": "1914",
                  "name": "1914"
                },
                {
                  "url": "/en/brand/1more",
                  "openNewTab": "",
                  "id": "1more",
                  "name": "1More"
                },
                {
                  "url": "/en/brand/3hk",
                  "openNewTab": "",
                  "id": "3hk",
                  "name": "3HK"
                },
                {
                  "url": "/en/brand/3uk",
                  "openNewTab": "",
                  "id": "3uk",
                  "name": "3UK"
                },
                {
                  "url": "/en/brand/4-pines",
                  "openNewTab": "",
                  "id": "4-pines",
                  "name": "4 Pines"
                },
                {
                  "url": "/en/brand/4smarts",
                  "openNewTab": "",
                  "id": "4smarts",
                  "name": "4smarts"
                }
              ],
              "code": "#"
            },
            {
              "brands": [
                {
                  "url": "/en/brand/ASUS",
                  "openNewTab": "",
                  "id": "ASUS",
                  "name": "ASUS"
                }
              ],
              "code": "A"
            },
            {
              "brands": [
                {
                  "url": "/en/brand/Braun",
                  "openNewTab": "",
                  "id": "Braun",
                  "name": "BRAUN"
                }
              ],
              "code": "B"
            },
            {
              "brands": [
                {
                  "url": "/en/brand/TomTom",
                  "openNewTab": "",
                  "id": "TomTom",
                  "name": "TOMTOM"
                }
              ],
              "code": "T"
            },
      
          
          ],
          "link": {
            "emptyMenu": false,
            "title": "Brands"
          },
          ":type": "ishop/components/home/brand"
        }
      },
      "sharafExperiences":{
        "linkText" :"See All Experiences",
        "linkUrl":"/",
         "link": {
            "emptyMenu": false,
            "title": "Sharaf Experiences"
          },
        "experiences":[
          {
            "image":"https://img.scaleflex.com/truck.jpg",
            "title":"Questions1",
            "description":"You can start typing on the left-hand text area and then click on the button.",
          },
           {
            "image":"https://img.scaleflex.com/sea-world.jpg",
            "title":"Techbench2",
            "description":"Let us set up your device.",
          },
           {
            "image":"https://img.scaleflex.com/room.jpg",
            "title":"Dg shield3",
            "description":"2+ years coverage for your devices.",
          },
           {
            "image":"https://img.scaleflex.com/truck.jpg",
            "title":"Questions4",
            "description":"You can start typing on the left-hand text area and then click on the button.",
          },
           {
            "image":"https://img.scaleflex.com/sea-world.jpg",
            "title":"Techbench5",
            "description":"Let us set up your device.",
          },
          {
            "image":"https://img.scaleflex.com/truck.jpg",
            "title":"Questions1",
            "description":"You can start typing on the left-hand text area and then click on the button.",
          },
           {
            "image":"https://img.scaleflex.com/sea-world.jpg",
            "title":"Techbench2",
            "description":"Let us set up your device.",
          },
    
        ],
      },
    },
            
    }
  },

  computed: {
    isThankYouPage () {
      return this.$store.state.checkout.isThankYouPage
        ? this.$store.state.checkout.isThankYouPage
        : false
    },      

  },
   updated () {
    this.autoHideHeader();
  },
  watch: {
    $route () {
      this.autoHideHeader();
    }
  },
  beforeMount () {
      window.addEventListener('scroll', () => {
      if (!this.scrolling) {
        this.scrolling = true;
        (!window.requestAnimationFrame)
          ? setTimeout(() => {
            this.autoHideHeader();
          }, 250)
          : requestAnimationFrame(() => {
            this.autoHideHeader();
          });
      }
    });
  },
  methods: { 
  
    gotoAccount () {
      this.$bus.$emit('modal-toggle', 'modal-signup')
    },
    autoHideHeader () {
      let currentTop = window.pageYOffset;
      this.checkStickyNavigation(currentTop);
      this.previousTop = currentTop;
      this.scrolling = false;
    },
     checkStickyNavigation (currentTop) {
      let HeaderElem = document.getElementsByTagName('header')[0].classList;
        if (currentTop > 0 && !this.isCheckoutPage) {
          HeaderElem.add('fixed');
        } else {
          HeaderElem.remove('fixed');
        }      
     },

  }
}
</script>

<style lang="scss" >
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
@import '~theme/css/helpers/mixins/font-face';
$color-icon-hover: color(secondary, $colors-background);

header {
  height: auto;
  top: 0px; 
  transition: top 0.2s ease-in-out;
  &.is-visible {
    top: 0;
  }
  @include font-face('Nunito Sans', 12px, normal, null); 
  
}
.search_icon{
    fill: color(black);
  }

// menu
.sub-nav-list{
  display: none;
}
.nav-list:hover + .sub-nav-list{
  display: flex;
}


.right-icons {
  //for edge
  float: right;
}
.header-placeholder {
  height: 72px;
}
.links {
  text-decoration: underline;
}
@media (max-width: 767px) {
  .row.middle-xs {
    margin: 0 -15px;

    &.py5 {
      margin: 0;
    }
  }
  .col-xs-2:first-of-type {
    padding-left: 0;
  }
  .col-xs-2:last-of-type {
    padding-right: 0;
  }
  a,
  span {
    font-size: 12px;
  }
}
.header-container{
  .material-icons, button{
    color: color(white);   
  }
  .icon{
    opacity: 1;
  }  
  .icon:hover, .icon:focus{
    background-color: color(transparent);
  }
}


.subcat-section{
  display:flex;
  flex-direction:column;
  flex-wrap:wrap;
  align-content:flex-start;
  overflow:auto;
  padding: 10px 15px;
}

@include media(md-down){
  .header__logo-wrapper{
    flex-basis: 7%;
  }
  .header__search-wrapper{
    flex-basis: 88%;
  }
  .header__right-wrapper{
    flex-basis: 5%;
  }
}
@include media(md-up){
  .header__logo-wrapper{
    flex-basis: 15%;
  }
  .header__search-wrapper{
    flex-basis: 50%;
  }
  .header__right-wrapper{
    flex-basis: 30%;
  }
}   
@include media(lg-up){
  .header__search-wrapper{
    flex-basis: 58%;
  }
  .header__right-wrapper{
    flex-basis: 22%;
  }
}  

</style>
