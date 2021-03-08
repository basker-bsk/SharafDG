<template>
    <nav >
      <div class="nav-container relative w-100 bg-white brdr-cl-secondary brdr-bottom-1">
        <div class="topnav-container container px-xs-0 px-md-10">
          <div class="row">
              <div class="col-md-2 col-lg-2 justify-space-between brdr-right-1 brdr-cl-secondary d-xs-none d-md-flex pointer align-item-center" 
              @mouseover="showMenu(categoryitems.categories.category.link.title);shopallHovering=true;"
               >
                  <a href="#" class="py-xs-12 link">{{categoryitems.categories.category.link.title}}</a>
                   <Icon class="list__arrow w-xs-12 h-xs-10 ml10" icon-id="downArrow" :class="{ 'active': shopallHovering }" />
              </div>
              <div class="col-md-7 col-lg-7 d-md-flex d-xs-none" >
                <ul class="levelone-menu d-xs-flex">
                  <!-- Brands -->
                   <li @mouseover="showMenu(categoryitems.brands.brand.link.title);isHovering=true;"                  
                  :class="{'menu-active':selectedCategory == categoryitems.brands.brand.link.title && isHovering}"
                  >
                    <a href="" class="link">{{categoryitems.brands.brand.link.title}}</a>
                  </li>
                  <!-- Sharaf Experiences -->
                  <li @mouseover="showMenu(categoryitems.sharafExperiences.link.title);isHovering=true;"                  
                  :class="{'menu-active':selectedCategory == categoryitems.sharafExperiences.link.title && isHovering}"
                  >
                    <a href="" class="link">{{categoryitems.sharafExperiences.link.title}}</a>
                  </li>                 
                </ul>
              </div>
              <div class="col-md-3 col-xs-12 col-lg-3 center-xs ">
                  <DeliveryCity ></DeliveryCity>
              </div>
          </div>
        </div>
        <div @mouseleave="hideMenu()" v-if="(selectedCategory === categoryitems.categories.category.link.title && isHovering)" >
            <ShopAllCategories  :categoryitems="categoryitems.categories.category.categoryItems"/> 
        </div>
         <!-- Brands -->
        <div @mouseleave="hideMenu()" v-if="(selectedCategory === categoryitems.brands.brand.link.title && isHovering)" >
            <Brands  :categoryitems="categoryitems.brands.brand"/> 
        </div>
        <!-- Sharaf Experiences -->
         <div @mouseleave="hideMenu()" v-if="(selectedCategory === categoryitems.sharafExperiences.link.title && isHovering)" >
            <SharafExperiences  :categoryitems="categoryitems.sharafExperiences"/> 
        </div>
       </div>
       <div v-if="isHovering" @click="isHovering = false" class="overlay" />
       <div v-if="isHovering" @mouseover="isHovering = false;shopallHovering=false" class="overlay overlay-top" />
    </nav>
</template>
<script>
import DeliveryCity from '../Shared/DeliveryCity'
import ShopAllCategories from "./ShopAllCategories"
import SharafExperiences from '../Shared/SharafExperiences'
import Brands from '../Shared/Brands'
import Icon from 'theme/components/custom/Global/Icon'

export default {
    name: 'Desktop-Menu',
    components: {
        DeliveryCity,
        SharafExperiences,
        ShopAllCategories,
        Brands,
        Icon
    },
    data () {
    return {
        isHovering:false,
        shopallHovering:false,
        sharafExperience:[],
        selectedCategory: String,
        CATEGORIES:String,
        BRANDS:String,
        SHARAF_EXPERIENCE:String,
      }
    },
    props: {
       categoryitems: {
        type: Object,
        required: true
        }
    },
    methods:{
      showMenu(category){
        this.selectedCategory = category
        this.isHovering = true
        this.shopallHovering=true
      },
      hideMenu(){
        this.selectedCategory = "";
        this.isHovering = false
        this.shopallHovering = false
      }
    },   
    watch: {
      $route () {
        this.isHelpMenuVisible = false;
      },
    },
}
</script>
<style  lang="scss">
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
.nav-container{
  font-size: 13px;
  a:after, a:hover:after{
    display: none;
  } 
  ul{
    list-style: none;
  }
  .menu-active{
    position: relative;
    &:before{
      content: '';
      border-bottom: 3px solid color(sdg-orange);
      width: 100%;
      position: absolute;
      bottom: -1px;
      left: 0;
    }
  }
}
.topnav-container{
  a{
    color: color(sdg-dark);
  }
}
.subnav-container{
  position: absolute;
  overflow: hidden;
  left: 0;
  display: block;
  background: color(white); 
  .subnav-wrapper{  
    overflow: hidden;
    height: 75vh;
  }
}
@media (min-width: 1300px) {
  .subnav-container{
    .sharaf-experiences{  
      overflow: hidden;
      height: 65vh;    
    }
  }
}
@media (min-width: 1400px) {
  .subnav-container{
    .sharaf-experiences{  
      overflow: hidden;
      height: 55vh;    
    }
  }
}
.nav-active .subnav-container{
  display: block;
}
.levelone-menu{
  li{
    padding: 15px 0;
    margin: 0 15px;    
    cursor: pointer;
  }
}
.overlay-top{
  height: 69px;
  top:0;
}
@include media(md-down){
    .nav-container + .overlay{
        top: 102px;
    }
}
@include media(md-up){
    .nav-container + .overlay{
        top: 118px;
    }
}
</style>