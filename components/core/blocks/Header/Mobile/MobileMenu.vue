<template>
     <div class="menulinks_wrapper">
        <ul class="level-1"> 
            <li class="bg-cl-primary cl-white px-xs-20 py-xs-20  d-xs-flex align-item-center justify-space-between " @click="openLevelOne = true"
            >
                <span class="cl-white" href="">{{shopallcategories.link.title}}</span>
                <Icon v-if="shopallcategories.categoryItems.length > 0" 
                class="list__arrow cl-white w-xs-12 h-xs-10" icon-id="RightArrow" />
            </li>
            <!-- <li class="bg-cl-primary cl-white px20 py-xs-20  d-xs-flex align-item-center justify-space-between">
                <router-link @click="openSidebarMenu = false"  class="no-underline block py10" :to="localizedRoute('/my-account')">Latest Arrivals</router-link>
            </li>    -->
            
        </ul>
        <ShopAllCategoriesMobile :shopallcategories="shopallcategories.categoryItems"/>
    </div>
</template>
<script>
import Icon from 'theme/components/custom/Global/Icon'
import ShopAllCategoriesMobile from './ShopAllCategoriesMobile'
export default {
    name:"MobileMenu",
    components: {
        Icon,
        ShopAllCategoriesMobile,
    },
     data(){
        return{
            openLevelOne:false,
            openSidebarMenu:false,
        }
    },
    props: {
       shopallcategories: {
        type: Object,
        required: true
        }
    },
      methods: {
        openMenu (){
            this.openSidebarMenu = !this.openSidebarMenu;
        },
        closeSidebarMenu (){
            this.openSidebarMenu = !this.openSidebarMenu;
        }, 
    },
}
</script>
<style scoped lang="scss">
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
.menulinks_wrapper{
    .icon{
      fill:color(white);
    }  
    a{
        color: color(white);
    }
    .level-1{
        > li{
            border-bottom: 1px solid rgba(255, 255, 255, .3);                
        }                       
    }
    .level-1.active{
        .level-2{
            left: 0;
            transition-duration: .25s;  
        }
    } 
}
</style>