<template>
     <div class="menulinks_wrapper">
        <ul class="level-1"> 
            <li class="bg-cl-primary cl-white px-xs-20 py-xs-20  d-xs-flex align-item-center justify-space-between " 
            @click="setSelectedCategory(shopallcategories.link.title)"
            >
                <span class="cl-white" href="">{{shopallcategories.link.title}}</span>
                <Icon v-if="shopallcategories.categoryItems.length > 0" 
                class="list__arrow white w-xs-12 h-xs-10" icon-id="RightArrow" />
            </li>  
            <li class="bg-cl-primary cl-white px-xs-20 py-xs-20  d-xs-flex align-item-center justify-space-between " 
            @click="setSelectedCategory(brands.link.title)"
            >
                <span class="cl-white" href="">{{brands.link.title}}</span>
                <Icon v-if="brands.brandList.length > 0" 
                class="list__arrow white w-xs-12 h-xs-10" icon-id="RightArrow" />
            </li>            
        </ul>

        <transition name="slide-left">
        <div v-if="(selectedCategory === categoriesTitle)"
        class="bg-cl-white z-xs-1 absolute h-100 w-100 top-0 left-0" >
            <ShopAllCategoriesMobile
                v-on:resetSelected="resetSelected"
                :data="shopallcategories.categoryItems"
                :title="shopallcategories.link.title"
            />
        </div>
       
        <div v-if="(selectedCategory === brandsTitle)"
        class="bg-cl-white z-xs-1 absolute h-100 w-100 top-0 left-0" >
            <BrandsMobile  
                v-on:resetSelected="resetSelected"
                :data="brands"
            />
        </div>
         </transition>
    </div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
import ShopAllCategoriesMobile from './ShopAllCategoriesMobile'
import BrandsMobile from './BrandsMobile'
export default {
    name:"MobileMenu",
    components: {
        Icon,
        ShopAllCategoriesMobile,
        BrandsMobile,
    },
     data(){
        return{
            openMenu:false,
            selectedCategory:String,
            categoriesTitle:this.shopallcategories.link.title,
            brandsTitle:this.brands.link.title,
        }
    },
    props: {
       shopallcategories: {
            type: Object,
            required: true
        },
        brands:{
            type:Object,
            required: true
        },        
    },
     methods: {
        setSelectedCategory (value){
            this.selectedCategory = value;
            this.openMenu= true;
        },
        resetSelected(){
            this.selectedCategory ='';
            this.openMenu = false;
        }
        

    },
}
</script>
<style lang="scss">
@import "~theme/css/animations/transitions";
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
.menulinks_wrapper{
    .level-1{
        > li{
            border-bottom: 1px solid rgba(255, 255, 255, .3);                
        }                       
    }

}

.slide-left-enter-active,
.slide-left-leave-active{
  transition: transform .25s;
  left:0;
}

.slide-left-enter,
.slide-left-leave-to {
  transform: translateX(-100%);
}
</style>