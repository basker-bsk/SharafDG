<template>
  <div class="header">
    <header class=" w-100 header header--banner ">
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
    Search
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
            {
              "httpStatusCode": 0,
              "url": "/en/category/womens-fashion",
              "id": "womens-fashion",
              "name": "Women's Fashion",
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
                  "url": "/en/category/womens-fashion",
                  "id": "womens-fashion-see-all",
                  "name": "See All"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/womens-fashion?newArrival=true",
                  "id": "womens-fashion|newArrival",
                  "name": "New Arrivals"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/womens-fashion",
                  "id": "womens-fashion-best-sellers",
                  "name": "Best Sellers"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/womens-fashion/womens-jewellery",
                  "id": "womens-jewellery",
                  "name": "Jewellery",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-jewellery/womens-jewellery-bracelets",
                      "id": "womens-jewellery-bracelets",
                      "name": "Bracelets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-jewellery/womens-jewellery-brooches",
                      "id": "womens-jewellery-brooches",
                      "name": "Brooches"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-jewellery/womens-jewellery-charms",
                      "id": "womens-jewellery-charms",
                      "name": "Charms"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-jewellery/womens-jewellery-earrings",
                      "id": "womens-jewellery-earrings",
                      "name": "Earrings"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-jewellery/womens-jewellery-necklace",
                      "id": "womens-jewellery-necklace",
                      "name": "Necklace"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-jewellery/womens-jewellery-rings",
                      "id": "womens-jewellery-rings",
                      "name": "Rings"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/womens-fashion/womens-shoes",
                  "id": "womens-shoes",
                  "name": "Shoes",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-shoes/womens-shoes-heels",
                      "id": "womens-shoes-heels",
                      "name": "Heels"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-shoes/womens-shoes-boots",
                      "id": "womens-shoes-boots",
                      "name": "Boots"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-shoes/womens-shoes-sneakers",
                      "id": "womens-shoes-sneakers",
                      "name": "Sneakers"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-shoes/womens-shoes-flats",
                      "id": "womens-shoes-flats",
                      "name": "Flats"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/womens-fashion/womens-watches",
                  "id": "womens-watches",
                  "name": "Watches",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-watches/womens-watches-fashion-watches",
                      "id": "womens-watches-fashion-watches",
                      "name": "Fashion Watches"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-watches/womens-watches-fine-watches",
                      "id": "womens-watches-fine-watches",
                      "name": "Fine Watches"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-watches/womens-watches-smart-watches",
                      "id": "womens-watches-smart-watches",
                      "name": "Smart Watches"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/womens-fashion/womens-accessories",
                  "id": "womens-accessories",
                  "name": "Accessories",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-accessories/womens-accessories-cardholders",
                      "id": "womens-accessories-cardholders",
                      "name": "CardHolders"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-accessories/womens-accessories-sunglasses",
                      "id": "womens-accessories-sunglasses",
                      "name": "Sunglasses"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-accessories/womens-accessories-wallets",
                      "id": "womens-accessories-wallets",
                      "name": "Wallets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-accessories/womens-accessories-belts",
                      "id": "womens-accessories-belts",
                      "name": "Belts"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/womens-fashion/womens-bags",
                  "id": "womens-bags",
                  "name": "Bags",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-bags/womens-bags-handbags",
                      "id": "womens-bags-handbags",
                      "name": "Handbags"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-bags/womens-bags-sling-bags",
                      "id": "womens-bags-sling-bags",
                      "name": "Sling Bags"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-bags/womens-bags-clutches",
                      "id": "womens-bags-clutches",
                      "name": "Clutches"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-bags/womens-bags-backpacks",
                      "id": "womens-bags-backpacks",
                      "name": "Backpacks"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/womens-fashion/womens-stationery",
                  "id": "womens-stationery",
                  "name": "Women's Stationery",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-stationery/womens-stationery-writing-instruments",
                      "id": "womens-stationery-writing-instruments",
                      "name": "Writing Instruments"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/womens-fashion/womens-designer-collection",
                  "id": "womens-designer-collection",
                  "name": "Designer Collection",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-designer-collection/womens-designer-collection-bags",
                      "id": "womens-designer-collection-bags",
                      "name": "Bags"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-designer-collection/womens-designer-collection-jewellery",
                      "id": "womens-designer-collection-jewellery",
                      "name": "Jewellery"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-designer-collection/womens-designer-collection-accessories",
                      "id": "womens-designer-collection-accessories",
                      "name": "Accessories"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-designer-collection/womens-designer-collection-shoes",
                      "id": "womens-designer-collection-shoes",
                      "name": "Shoes"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/womens-fashion/womens-stationary",
                  "id": "womens-stationary",
                  "name": "Stationary",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/womens-fashion/womens-stationary/womens-stationary-writing-instruments",
                      "id": "womens-stationary-writing-instruments",
                      "name": "Writing Instruments"
                    }
                  ]
                }
              ]
            },
            {
              "httpStatusCode": 0,
              "url": "/en/category/health-and-wellness",
              "id": "health-and-wellness",
              "name": "Health & Wellness",
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
                  "url": "/en/category/health-and-wellness",
                  "id": "health-and-wellness-see-all",
                  "name": "See All"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/health-and-wellness?newArrival=true",
                  "id": "health-and-wellness|newArrival",
                  "name": "New Arrivals"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/health-and-wellness?giftAndValueSet=true",
                  "id": "health-and-wellness|giftAndValueSet",
                  "name": "Gifts & Values Sets"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/health-and-wellness?travelExclusive=true",
                  "id": "health-and-wellness|travelExclusive",
                  "name": "Travel Exclusives"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/health-and-wellness?promo=true",
                  "id": "health-and-wellness|promo",
                  "name": "Sale"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/health-and-wellness/personal-care",
                  "id": "personal-care",
                  "name": "Personal Care",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/personal-care/personal-care-family-planning",
                      "id": "personal-care-family-planning",
                      "name": "Family Planning"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/personal-care/personal-care-deodorant",
                      "id": "personal-care-deodorant",
                      "name": "Deodorant"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/personal-care/personal-care-ent-care",
                      "id": "personal-care-ent-care",
                      "name": "ENT Care"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/personal-care/personal-care-oral-and-dental",
                      "id": "personal-care-oral-and-dental",
                      "name": "Oral & Dental"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/personal-care/personal-care-massager",
                      "id": "personal-care-massager",
                      "name": "Massager"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/health-and-wellness/medication-and-treatement",
                  "id": "medication-and-treatement",
                  "name": "Medication & Treatement",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/medication-and-treatement/medication-and-treatement-paracetamols",
                      "id": "medication-and-treatement-paracetamols",
                      "name": "Paracetalmols"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/medication-and-treatement/medication-and-treatement-cough",
                      "id": "medication-and-treatement-cough",
                      "name": "Cough"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/medication-and-treatement/medication-and-treatement-ointments",
                      "id": "medication-and-treatement-ointments",
                      "name": "Ointments"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/medication-and-treatement/medication-and-treatement-flu",
                      "id": "medication-and-treatement-flu",
                      "name": "Flu"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/medication-and-treatement/medication-and-treatement-spray",
                      "id": "medication-and-treatement-spray",
                      "name": "Spray"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/health-and-wellness/supplements-and-nutrients",
                  "id": "supplements-and-nutrients",
                  "name": "Supplements & Nutrients",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/supplements-and-nutrients/supplements-and-nutrients-vitamins",
                      "id": "supplements-and-nutrients-vitamins",
                      "name": "Vitamins"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/supplements-and-nutrients/supplements-and-nutrients-sports",
                      "id": "supplements-and-nutrients-sports",
                      "name": "Sports"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/supplements-and-nutrients/supplements-and-nutrients-women",
                      "id": "supplements-and-nutrients-women",
                      "name": "Women"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/health-and-wellness/herbs-and-traditional-medicine",
                  "id": "herbs-and-traditional-medicine",
                  "name": "Herbs & Traditional Medicine",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/herbs-and-traditional-medicine/herbs-and-traditional-medicine-bird-nest",
                      "id": "herbs-and-traditional-medicine-bird-nest",
                      "name": "Bird Nest"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/herbs-and-traditional-medicine/herbs-and-traditional-medicine-collagen",
                      "id": "herbs-and-traditional-medicine-collagen",
                      "name": "Collagen"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/herbs-and-traditional-medicine/herbs-and-traditional-medicine-tonics",
                      "id": "herbs-and-traditional-medicine-tonics",
                      "name": "Tonics"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/health-and-wellness/firstaid-and-medical-supplies",
                  "id": "firstaid-and-medical-supplies",
                  "name": "FirstAid & Medical Supplies",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/firstaid-and-medical-supplies/firstaid-and-medical-supplies-firstaid-kit",
                      "id": "firstaid-and-medical-supplies-firstaid-kit",
                      "name": "FirstAid Kit"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/health-and-wellness/firstaid-and-medical-supplies/firstaid-and-medical-supplies-plasters-and-patches",
                      "id": "firstaid-and-medical-supplies-plasters-and-patches",
                      "name": "Plasters & Patches"
                    }
                  ]
                }
              ]
            },
            {
              "httpStatusCode": 0,
              "url": "/en/category/wine-and-spirits",
              "id": "wine-and-spirits",
              "name": "Wine & Spirits",
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
                  "url": "/en/category/wine-and-spirits",
                  "id": "wine-and-spirit-see-all",
                  "name": "See All"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/wine-and-spirits?newArrival=true",
                  "id": "wine-and-spirits|newArrival",
                  "name": "New Arrivals"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/wine-and-spirits/wine",
                  "id": "wine",
                  "name": "Wine",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/wine/wine-champagne",
                      "id": "wine-champagne",
                      "name": "Champagne"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/wine/wine-sparkling-wine",
                      "id": "wine-sparkling-wine",
                      "name": "Sparkling Wine"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/wine/wine-dessert-wine",
                      "id": "wine-dessert-wine",
                      "name": "Dessert Wine"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/wine/wine-fortified-wine",
                      "id": "wine-fortified-wine",
                      "name": "Fortified Wine"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/wine/wine-red-wine",
                      "id": "wine-red-wine",
                      "name": "Red Wine"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/wine/wine-sake",
                      "id": "wine-sake",
                      "name": "Sake"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/wine/wine-sweet-wine",
                      "id": "wine-sweet-wine",
                      "name": "Sweet Wine"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/wine/wine-white-wine",
                      "id": "wine-white-wine",
                      "name": "White Wine"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/wine/wine-rose-wine",
                      "id": "wine-rose-wine",
                      "name": "Rose Wine"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/wine-and-spirits/spirits",
                  "id": "spirits",
                  "name": "Spirits",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-armagnac",
                      "id": "spirits-armagnac",
                      "name": "Armagnac"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-baijju",
                      "id": "spirits-baijju",
                      "name": "Baijiu"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-bourbon",
                      "id": "spirits-bourbon",
                      "name": "Bourbon"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-brandy",
                      "id": "spirits-brandy",
                      "name": "Brandy"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-whisky",
                      "id": "spirits-whisky",
                      "name": "Whisky"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-gin",
                      "id": "spirits-gin",
                      "name": "Gin"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-cognac",
                      "id": "spirits-cognac",
                      "name": "Cognac"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-liquers",
                      "id": "spirits-liquers",
                      "name": "Liqueurs"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-scotch",
                      "id": "spirits-scotch",
                      "name": "Scotch"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-rum",
                      "id": "spirits-rum",
                      "name": "Rum"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-single",
                      "id": "spirits-single",
                      "name": "Single"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-malt",
                      "id": "spirits-malt",
                      "name": "Malt"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-tequilla",
                      "id": "spirits-tequilla",
                      "name": "Tequila"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-vodka",
                      "id": "spirits-vodka",
                      "name": "Vodka"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/spirits/spirits-japanese-whisky",
                      "id": "spirits-japanese-whisky",
                      "name": "Japanese Whiskey"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/wine-and-spirits/beers",
                  "id": "beers",
                  "name": "Beers",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/beers/beers-belgian",
                      "id": "beers-belgian",
                      "name": "Belgian"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/beers/beers-cider",
                      "id": "beers-cider",
                      "name": "Cider"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/beers/beers-lager",
                      "id": "beers-lager",
                      "name": "Lager"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/beers/beers-pale-ale",
                      "id": "beers-pale-ale",
                      "name": "Pale Ale"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/wine-and-spirits/beers/beers-stout-craft",
                      "id": "beers-stout-craft",
                      "name": "Stout Craft"
                    }
                  ]
                }
              ]
            },
            {
              "httpStatusCode": 0,
              "url": "/en/category/mens-fashion",
              "id": "mens-fashion",
              "name": "Men's Fashion",
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
                  "url": "/en/category/mens-fashion",
                  "id": "mens-fashion-see-all",
                  "name": "See All"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/mens-fashion?newArrival=true",
                  "id": "mens-fashion|newArrival",
                  "name": "New Arrivals"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/mens-fashion",
                  "id": "mens-fashion-best-sellers",
                  "name": "Best Sellers"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/wine-and-spirit?giftAndValueSet=true",
                  "id": "wine-and-spirit|giftAndValueSet",
                  "name": "Gifts & Values Sets"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/wine-and-spirit?travelExclusive=true",
                  "id": "wine-and-spirit|travelExclusive",
                  "name": "Travel Exclusives"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/wine-and-spirit?promo=true",
                  "id": "wine-and-spirit|promo",
                  "name": "Sale"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/mens-fashion/mens-shoes",
                  "id": "mens-shoes",
                  "name": "Shoes",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-shoes/mens-shoes-boots",
                      "id": "mens-shoes-boots",
                      "name": "Boots"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-shoes/mens-shoes-sneakers",
                      "id": "mens-shoes-sneakers",
                      "name": "Sneakers"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-shoes/mens-shoes-flats",
                      "id": "mens-shoes-flats",
                      "name": "Flats"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/mens-fashion/mens-jewellery",
                  "id": "mens-jewellery",
                  "name": "Jewellery",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-jewellery/mens-jewellery-bracelets",
                      "id": "mens-jewellery-bracelets",
                      "name": "Bracelets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-jewellery/mens-jewellery-cufflinks",
                      "id": "mens-jewellery-cufflinks",
                      "name": "Cufflinks"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/mens-fashion/mens-watches",
                  "id": "mens-watches",
                  "name": "Watches",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-watches/mens-watches-fashion-watches",
                      "id": "mens-watches-fashion-watches",
                      "name": "Fashion Watches"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-watches/mens-watches-fine-watches",
                      "id": "mens-watches-fine-watches",
                      "name": "Fine Watches"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-watches/mens-watches-smart-watches",
                      "id": "mens-watches-smart-watches",
                      "name": "Smart Watches"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/mens-fashion/mens-bags",
                  "id": "mens-bags",
                  "name": "Bags",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-bags/mens-bags-crossbody",
                      "id": "mens-bags-crossbody",
                      "name": "Crossbody"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-bags/mens-bags-sling",
                      "id": "mens-bags-sling",
                      "name": "Sling"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-bags/mens-bags-backpacks",
                      "id": "mens-bags-backpacks",
                      "name": "Backpacks"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-bags/mens-bags-duffel",
                      "id": "mens-bags-duffel",
                      "name": "Duffel"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-bags/mens-bags-foldable",
                      "id": "mens-bags-foldable",
                      "name": "Foldable"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-bags/mens-bags-laptops",
                      "id": "mens-bags-laptops",
                      "name": "Laptops"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-bags/mens-bags-briefcases",
                      "id": "mens-bags-briefcases",
                      "name": "Briefcases"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/mens-fashion/mens-accessories",
                  "id": "mens-accessories",
                  "name": "Accessories",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-accessories/mens-accessories-cardholders",
                      "id": "mens-accessories-cardholders",
                      "name": "CardHolders"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-accessories/mens-accessories-sunglasses",
                      "id": "mens-accessories-sunglasses",
                      "name": "Sunglasses"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-accessories/mens-accessories-wallets",
                      "id": "mens-accessories-wallets",
                      "name": "Wallets"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-accessories/mens-accessories-belts",
                      "id": "mens-accessories-belts",
                      "name": "Belts"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/mens-fashion/mens-stationery",
                  "id": "mens-stationery",
                  "name": "Men's Stationery",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-stationery/mens-stationery-writing-instruments",
                      "id": "mens-stationery-writing-instruments",
                      "name": "Writing Instruments"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/mens-fashion/mens-designer-collection",
                  "id": "mens-designer-collection",
                  "name": "Designer Collection",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-designer-collection/mens-designer-collection-bags",
                      "id": "mens-designer-collection-bags",
                      "name": "Bags"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-designer-collection/mens-designer-collection-jewellery",
                      "id": "mens-designer-collection-jewellery",
                      "name": "Jewellery"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-designer-collection/mens-designer-collection-accessories",
                      "id": "mens-designer-collection-accessories",
                      "name": "Accessories"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-designer-collection/mens-designer-collection-shoes",
                      "id": "mens-designer-collection-shoes",
                      "name": "Shoes"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/mens-fashion/mens-stationary",
                  "id": "mens-stationary",
                  "name": "Stationary",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/mens-fashion/mens-stationary/mens-stationary-writing-instruments",
                      "id": "mens-stationary-writing-instruments",
                      "name": "Writing Instruments"
                    }
                  ]
                }
              ]
            },
            {
              "httpStatusCode": 0,
              "url": "/en/category/baby-and-kids",
              "id": "baby-and-kids",
              "name": "Baby & Kids",
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
                  "url": "/en/category/baby-and-kids",
                  "id": "baby-and-kids-see-all",
                  "name": "See All"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/baby-and-kids?newArrival=true",
                  "id": "baby-and-kids|newArrival",
                  "name": "New Arrivals"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/baby-and-kids?giftAndValueSet=true",
                  "id": "baby-and-kids|giftAndValueSet",
                  "name": "Gifts & Values Sets"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/baby-and-kids?travelExclusive=true",
                  "id": "baby-and-kids|travelExclusive",
                  "name": "Travel Exclusives"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/baby-and-kids?promo=true",
                  "id": "baby-and-kids|promo",
                  "name": "Sale"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/baby-and-kids/baby-and-maternity",
                  "id": "baby-and-maternity",
                  "name": "Baby & Maternity",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/baby-and-maternity/baby-and-maternity-nursing-clothes",
                      "id": "baby-and-maternity-nursing-clothes",
                      "name": "Nursing Clothes"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/baby-and-maternity/baby-and-maternity-strollers",
                      "id": "baby-and-maternity-strollers",
                      "name": "Strollers"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/baby-and-maternity/baby-and-maternity-high-chairs",
                      "id": "baby-and-maternity-high-chairs",
                      "name": "High Chairs"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/baby-and-maternity/baby-and-maternity-booster-seats",
                      "id": "baby-and-maternity-booster-seats",
                      "name": "Booster Seats"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/baby-and-kids/kids-fashion",
                  "id": "kids-fashion",
                  "name": "Kids Fashion",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/kids-fashion/kids-fashion-girls-tops",
                      "id": "kids-fashion-girls-tops",
                      "name": "Girls Tops"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/kids-fashion/kids-fashion-boys-tops",
                      "id": "kids-fashion-boys-tops",
                      "name": "Boys Tops"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/kids-fashion/kids-fashion-boys-shorts",
                      "id": "kids-fashion-boys-shorts",
                      "name": "Boys Shorts"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/kids-fashion/kids-fashion-girls-shorts",
                      "id": "kids-fashion-girls-shorts",
                      "name": "Girls Shorts"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/kids-fashion/kids-fashion-dresses",
                      "id": "kids-fashion-dresses",
                      "name": "Dresses"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/kids-fashion/kids-fashion-shoes",
                      "id": "kids-fashion-shoes",
                      "name": "Shoes"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/baby-and-kids/feeding",
                  "id": "feeding",
                  "name": "Feeding",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/feeding/feeding-milk-powder",
                      "id": "feeding-milk-powder",
                      "name": "Milk Powder"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/feeding/feeding-bottle-feeding",
                      "id": "feeding-bottle-feeding",
                      "name": "Bottle Feeding"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/feeding/feeding-breast-feeding",
                      "id": "feeding-breast-feeding",
                      "name": "Breast Feeding"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/baby-and-kids/health-and-home-safety",
                  "id": "health-and-home-safety",
                  "name": "Health & Home Safety",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/health-and-home-safety/health-and-home-safety-health-supplements",
                      "id": "health-and-home-safety-health-supplements",
                      "name": "Health Supplements"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/baby-and-kids/health-and-home-safety/health-and-home-safety-safety-gate",
                      "id": "health-and-home-safety-safety-gate",
                      "name": "Safety Gate"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/baby-and-kids/stationaries",
                  "id": "stationaries",
                  "name": "Stationaries"
                }
              ]
            },
            {
              "httpStatusCode": 0,
              "url": "/en/category/travel",
              "id": "travel",
              "name": "Travel",
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
                  "url": "/en/category/travel",
                  "id": "travel-see-all",
                  "name": "See All"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/travel?newArrival=true",
                  "id": "travel|newArrival",
                  "name": "New Arrivals"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/travel?giftAndValueSet=true",
                  "id": "travel|giftAndValueSet",
                  "name": "Gifts & Values Sets"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/travel?travelExclusive=true",
                  "id": "travel|travelExclusive",
                  "name": "Travel Exclusives"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/travel?promo=true",
                  "id": "travel|promo",
                  "name": "Sale"
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/travel/travel-essentials",
                  "id": "travel-essentials",
                  "name": "Travel Essentials",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-essentials/travel-essentials-neck-pillows",
                      "id": "travel-essentials-neck-pillows",
                      "name": "Neck Pillow"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-essentials/travel-essentials-notebooks",
                      "id": "travel-essentials-notebooks",
                      "name": "Notebooks"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-essentials/travel-essentials-packing-organisers",
                      "id": "travel-essentials-packing-organisers",
                      "name": "Packing Organisers"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-essentials/travel-essentials-passport-holders",
                      "id": "travel-essentials-passport-holders",
                      "name": "Passport Holders"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-essentials/travel-essentials-towels",
                      "id": "travel-essentials-towels",
                      "name": "Towels"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-essentials/travel-essentials-water-bottles",
                      "id": "travel-essentials-water-bottles",
                      "name": "Water Bottles"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-essentials/travel-essentials-anti-theft-wallet",
                      "id": "travel-essentials-anti-theft-wallet",
                      "name": "Anti-Theft Wallet"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-essentials/travel-essentials-locks",
                      "id": "travel-essentials-locks",
                      "name": "Locks"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/travel/luggages",
                  "id": "luggages",
                  "name": "Luggages",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/luggages/luggages-carryons",
                      "id": "luggages-carryons",
                      "name": "Carry Ons"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/luggages/luggages-covers",
                      "id": "luggages-covers",
                      "name": "Covers"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/travel/bags",
                  "id": "bags",
                  "name": "Bags",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/bags/bags-backpacks",
                      "id": "bags-backpacks",
                      "name": "Backpacks"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/bags/bags-crossbody",
                      "id": "bags-crossbody",
                      "name": "Crossbody"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/bags/bags-duffel",
                      "id": "bags-duffel",
                      "name": "Duffel"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/bags/bags-foldable-bag",
                      "id": "bags-foldable-bag",
                      "name": "Foldable Bag"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/bags/bags-briefcase",
                      "id": "bags-briefcase",
                      "name": "Briefcase"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/bags/bags-laptop-case",
                      "id": "bags-laptop-case",
                      "name": "Laptop Case"
                    }
                  ]
                },
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/travel/travel-electronics",
                  "id": "travel-electronics",
                  "name": "Electronics",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-electronics/travel-electronics-adapters",
                      "id": "travel-electronics-adapters",
                      "name": "Adapter"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-electronics/travel-electronics-wifi-routers",
                      "id": "travel-electronics-wifi-routers",
                      "name": "Wifi Routers"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-electronics/travel-electronics-power-banks",
                      "id": "travel-electronics-power-banks",
                      "name": "Power Banks"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-electronics/travel-electronics-storage-devices",
                      "id": "travel-electronics-storage-devices",
                      "name": "Storage Devices"
                    },
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/travel/travel-electronics/travel-electronics-chargers",
                      "id": "travel-electronics-chargers",
                      "name": "Chargers"
                    }
                  ]
                }
              ]
            },
            {
              "httpStatusCode": 0,
              "url": "/en/category/Democategory",
              "id": "Democategory",
              "name": "Democategory",
              "subcategories": [
                {
                  "httpStatusCode": 0,
                  "url": "/en/category/Democategory/democatL2",
                  "id": "democatL2",
                  "name": "democatL2",
                  "subcategories": [
                    {
                      "httpStatusCode": 0,
                      "url": "/en/category/Democategory/democatL2/democatL3",
                      "id": "democatL3",
                      "name": "democatL3"
                    }
                  ]
                }
              ]
            }
          ],
          "link": {
            "emptyMenu": false,
            "title": "Shop All Categories123"
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
              "brandLogo": "https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/160/openmoji/272/apple-logo_f8ff.png"
            },
            {
              "redirectUrl": "/en/brand/chanel",
              "name": "Samsung",
              "code": "samsung",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://www.freepnglogos.com/uploads/blue-samsung-logo-png-4.png"
            },
            {
              "redirectUrl": "/en/brand/tissot",
              "name": "Dell",
              "code": "Dell",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://www.freepnglogos.com/uploads/dell-png-logo/world-brand-dell-png-logo-5.png"
            },
            {
              "redirectUrl": "/en/brand/apple",
              "name": "Apple",
              "code": "apple",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/160/openmoji/272/apple-logo_f8ff.png"
            },
            {
              "redirectUrl": "/en/brand/chanel",
              "name": "Samsung",
              "code": "samsung",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://www.freepnglogos.com/uploads/blue-samsung-logo-png-4.png"
            },
            {
              "redirectUrl": "/en/brand/tissot",
              "name": "Dell",
              "code": "Dell",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://www.freepnglogos.com/uploads/dell-png-logo/world-brand-dell-png-logo-5.png"
            },
            {
              "redirectUrl": "/en/brand/apple",
              "name": "Apple",
              "code": "apple",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/160/openmoji/272/apple-logo_f8ff.png"
            },
            {
              "redirectUrl": "/en/brand/chanel",
              "name": "Samsung",
              "code": "samsung",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://www.freepnglogos.com/uploads/blue-samsung-logo-png-4.png"
            },
            {
              "redirectUrl": "/en/brand/tissot",
              "name": "Dell",
              "code": "Dell",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://www.freepnglogos.com/uploads/dell-png-logo/world-brand-dell-png-logo-5.png"
            },
            {
              "redirectUrl": "/en/brand/apple",
              "name": "Apple",
              "code": "apple",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://emojipedia-us.s3.dualstack.us-west-1.amazonaws.com/thumbs/160/openmoji/272/apple-logo_f8ff.png"
            },
            {
              "redirectUrl": "/en/brand/chanel",
              "name": "Samsung",
              "code": "samsung",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://www.freepnglogos.com/uploads/blue-samsung-logo-png-4.png"
            },
            {
              "redirectUrl": "/en/brand/tissot",
              "name": "Dell",
              "code": "Dell",
              "altText": "",
              "openNewTab": "",
              "brandLogo": "https://www.freepnglogos.com/uploads/dell-png-logo/world-brand-dell-png-logo-5.png"
            }
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
  z-index: 10;  
  transition: top 0.2s ease-in-out;
  &.is-visible {
    top: 0;
  }
  @include font-face('Nunito Sans', 12px, bold, null); 
  
}
.search_icon{
    fill: color(black);
  }
.header__right-wrapper{
    .icon{
      fill: color(white);
    }    
  .dropdown-content .icon{
      fill: color(black);
  }
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
.myaccountlinks_wrapper, .header__search-wrapper{
    .icon{
      fill:color(black);
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
.header__right-wrapper{
  .language_wrapper{
      .icon{
          fill: color(black);
      }      
  }
}
</style>
