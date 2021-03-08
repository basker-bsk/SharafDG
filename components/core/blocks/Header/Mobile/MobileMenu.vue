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
        </ul>
        <ShopAllCategoriesMobile 
            :data="shopallcategories.categoryItems"
            :categorySelected="(selectedCategory === shopallcategories.link.title)"            
            :isMenuOpen="isMenuOpen"
        />
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
            selectedCategory:String,
            isMenuOpen:false,
            categorySelected:Boolean,
        }
    },
    props: {
       shopallcategories: {
        type: Object,
        required: true
        }
    },
      methods: {
        setSelectedCategory (value){
            this.selectedCategory = value;
            this.isMenuOpen = true;
        },
        resetSelectedCategory (){
            this.selectedCategory = '';
            return true
        }, 
    },
}
</script>
<style scoped lang="scss">
@import '~theme/css/variables/variables';
@import '~theme/css/helpers/functions/color';
.menulinks_wrapper{
 
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